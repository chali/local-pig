#Apache Pig Docker image

Do you want to execute Pig grunt? You can use this docker image which is useful
for playing with Pig. It doesn't support running agains hadoop in distributed
mode.

###Execution
Get docker image

    docker pull chalimartines/local-pig

Run grunt with specified folder sharing. Replace /your/host/dir/with/data with path where you have data.

    docker run --rm -it -v /your/host/dir/with/data:/data:rw chalimartines/local-pig

Then you can use folder /data in your LOAD command.

    x = LOAD '/data/your_file.csv' USING PigStorage();

Run pig script.

    docker run --rm -it -v /your/host/dir/with/data:/data:rw chalimartines/local-pig /data/your_script.pig

Note that pig script has to be in some shared folder and all data links
have to point to shared folders.

How to run image with access to Pig logs. Replace /your/host/logs/dir where you would like read logs on your host machine.

    docker run --rm -it -v /your/host/dir/with/data:/data:rw -v /your/host/logs/dir:/logs chalimartines/local-pig
