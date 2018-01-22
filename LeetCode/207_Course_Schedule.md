# 207. Course Schedule
Course Schedule

## Code
    public class Solution {
        public bool CanFinish(int numCourses, int[,] prerequisites) {
            List<List<int>> graph = new List<List<int>>();
            for(int i = 0; i < numCourses;i++) {
                List<int> list = new List<int>();
                graph.Add(list);
            }
            bool[] visited = new bool[numCourses];
            for(int i = 0; i < prerequisites.GetLength(0); i++){
                graph[prerequisites[i,1]].Add(prerequisites[i,0]);
            }

            for(int i = 0; i < numCourses; i ++){
                if(!DFSCourse(graph, visited, i))
                    return false;
            }
            return true;
        }
        
        private bool DFSCourse(List<List<int>> graph, bool[] visited, int course){
            if(visited[course])
                return false;
            else
                visited[course] = true;

            for(int i = 0; i < graph[course].Count; i++){
                if(!DFSCourse(graph, visited, (int)graph[course][i]))
                    return false;
            }
            visited[course] = false;
            return true;
        }
    }