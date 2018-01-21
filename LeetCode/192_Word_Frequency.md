# 192. Word Frequency
Word Frequency

## Code
    # Read from the file words.txt and output the word frequency list to stdout.
    # need repeat
    cat words.txt | tr -s ' ' '\n' | sort | uniq -c | sort -r | awk '{ print $2, $1 }'