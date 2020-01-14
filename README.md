# TOP_1
TopK-URL
Context
This demo implements an algorithm for processing massive amounts of data => hahsmap + min-heap. This project uses a url file as an example, assuming the file size is 100G. We need to find the top K urls that have the most occurrences in all urls with a machine with only 1G of memory.

Implementation
We use streaming data to process very large files and use the BKDRHash function to assign different urls into different files. But make sure that the same url in the huge file needs to appear in the same file.

Then, we calculate a Top100 min-heap for each file.

In the end, we merge all the min-heap into one min-heap.

Key parameters
NUM_FILE: This is the number of files after splitting. We set the default value to 100

NUM_TOP: It represents K in TopK. We set the default value to 100

SIZE_BATCH: Our default url is 255 bytes on average. Because we have a 1G memory limit, we set the Batch_size to 390,0000.

Optimization
For reducing IO times/system calls and using 1G of memory, we take batch operations as much as possible.

How to Use
Lauch
We already have the sample data set "Dataset.txt". You can replace it as needed. Please enter the project root directory and execute the following command

$ go run main.go 

The top 100 results have been output to file "./output.txt"
App elapsed:  641.453417ms
Normally, you can find the TopK urls results in the file "output.txt". "./tmp" is used to store the split file. If you want to retest, you can execute clear.sh to remove tmp and output.
