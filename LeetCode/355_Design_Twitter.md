# 355. Design Twitter
Design Twitter

## Code
    public class Tweet {
        public int userId;
        public int id;
        public long time;
        public Tweet(int id, long time, int userId) {
            this.id = id;
            this.time = time;
            this.userId = userId;
        }
    }


    public class Twitter {

        public Dictionary<int, List<int>> fansDic;
        public Dictionary<int, List<Tweet>> userTweetIdDic;
        public long time = 0;
        /** Initialize your data structure here. */
        public Twitter() {
            fansDic = new Dictionary<int, List<int>>();
            userTweetIdDic = new Dictionary<int, List<Tweet>>();
        }
        
        /** Compose a new tweet. */
        public void PostTweet(int userId, int tweetId) {
            time ++;
            Tweet tweet = new Tweet(tweetId, time, userId);
            if(userTweetIdDic.ContainsKey(userId)) {
                userTweetIdDic[userId].Insert(0, tweet);
            }else {
                userTweetIdDic.Add(userId, new List<Tweet>(){tweet});
            }
            //userTweetIdDic[userId].Sort(Compare);
            if(fansDic.ContainsKey(userId)) {
                List<int> fansList = fansDic[userId];
                for(int i = 0; i < fansList.Count; i ++) {
                    if(userTweetIdDic.ContainsKey(fansList[i])) {
                        if(!userTweetIdDic[fansList[i]].Contains(tweet))
                            userTweetIdDic[fansList[i]].Add(tweet);
                    }else {
                        userTweetIdDic.Add(fansList[i], new List<Tweet>(){tweet});
                    }
                }

            } 
        }
        
        /** Retrieve the 10 most recent tweet ids in the user's news feed. Each item in the news feed must be posted by users who the user followed or by the user herself. Tweets must be ordered from most recent to least recent. */
        public IList<int> GetNewsFeed(int userId) {
            IList<int> res = new List<int>();
            if(userTweetIdDic.ContainsKey(userId)) {
                userTweetIdDic[userId].Sort(Compare);
                List<Tweet> list = userTweetIdDic[userId];
            
                for(int i = 0; i < list.Count; i ++) {
                    if(i < 10)
                        res.Add(list[i].id);
                    else 
                        break;
                }
            }

            return res;
        }
        
        /** Follower follows a followee. If the operation is invalid, it should be a no-op. */
        public void Follow(int followerId, int followeeId) {
            if(followerId == followeeId)
                return;
            if(fansDic.ContainsKey(followeeId)){
                fansDic[followeeId].Add(followerId);
            }else {
                fansDic.Add(followeeId, new List<int>(){followerId});
            }
            
            if(!userTweetIdDic.ContainsKey(followerId)) {
                userTweetIdDic.Add(followerId, new List<Tweet>());
            }
            if(userTweetIdDic.ContainsKey(followeeId)) {
                List<Tweet> list = userTweetIdDic[followeeId];
                for(int i = 0; i < list.Count; i ++) {
                    if(list[i].userId == followeeId) {
                        if(!userTweetIdDic[followerId].Contains(list[i]))
                            userTweetIdDic[followerId].Add(list[i]);
                    }
                }
            }
        }
        
        /** Follower unfollows a followee. If the operation is invalid, it should be a no-op. */
        public void Unfollow(int followerId, int followeeId) {
            if(followerId == followeeId)
                return;
            
            if(fansDic.ContainsKey(followeeId)) {
                fansDic[followeeId].Remove(followerId);
            }
            if(userTweetIdDic.ContainsKey(followerId)) {
                List<Tweet> list = userTweetIdDic[followerId];
                list.RemoveAll(j => j.userId == followeeId);
                
            }
        }
        
        public int Compare(Tweet tweet1, Tweet tweet2){
            if(tweet1.time > tweet2.time)
                return -1;
            else if(tweet1.time < tweet2.time)
                return 1;
            else 
                return 0;
        }
    }


    /**
    * Your Twitter object will be instantiated and called as such:
    * Twitter obj = new Twitter();
    * obj.PostTweet(userId,tweetId);
    * IList<int> param_2 = obj.GetNewsFeed(userId);
    * obj.Follow(followerId,followeeId);
    * obj.Unfollow(followerId,followeeId);
    */