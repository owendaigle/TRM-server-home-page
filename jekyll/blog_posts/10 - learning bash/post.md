---
layout: post
title: Learning Bash
post_date: 2025/03/28
update_date: 2025/03/28
topic: Code
author: Owen Daigle

---

I have recently been writing a few scripts in bash such as my [minecraft AFK script](https://github.com/owendaigle/minecraft-afk-script-linux) and a few other simple ones such as to change power profiles on laptop, or disable touchpad through keyboard shortcut. 

I have been wanting to get better at bash scripting for awhile, so over the past few days I have tried to make some simple scripts to run some of my programs made for school. I know that this takes up more of my precious time since I could just go ahead and run the code itself with no problems, but this is more fun. 

I recently just made a decent size script which basically compiles a couple of java projects, and then runs each of those projects with arguments n times (where n is a constant) and saves some of the code output from each of those runs. Then at the end it calculates the average efficiency of all these runs which is important because the programs are kind of random, but as the number of trials increases, the sample mean approaches the real mean. 

Now I could have done this manually, just run the program a few thousand times, or just done this through java, but it is kind of cool to do it not from within java and to make a script to do it!!!

Should I have done this, probably not. It would have been faster to do it in java which I am familiar with. But was it fun and cool, YES DEFINITELY. Also I can use these skills in other projects if I want. 

```bash
#! /bin/bash
#This is the number of queens to search for, higher is longer. 
#Does not work with values of 2 or 3
NUMBEROFQUEENS=5
#This is the number of times to run the test. Ideally larger is better, but takes longer.
NUMBEROFRUNS=30

currentdir="$PWD"
singleThreadResult=() # stores all runs
multiThreadResult=()
average=0 #stores single thread average
Multiaverage=0 # stores multi thread average

cd "$currentdir/8-Queen Problem HC Single Thread/"
# compiles
javac *.java

if [ $? -eq 0 ]
then
    echo "Compiled Successfully"
else
    echo "Failed to compile"
    exit 1
fi

echo "Running with $NUMBEROFQUEENS queens and $NUMBEROFRUNS runs"
echo

#### SINGLE THREADED BENCHMARKS


# run many times
for ((i=0; i<= ($NUMBEROFRUNS-1); i++))
do
    singleThreadResult+=("$(java Main "$NUMBEROFQUEENS" | tail -n 1)")
    average=$((average + singleThreadResult[i])) #calculate average
    if [ $NUMBEROFQUEENS -gt 30 ] #show progress for lots of queens
    then
        echo "Running"
    fi

done

# actually calculate average
average=$((average / NUMBEROFRUNS))


##### Multi Thread

cd "$currentdir/8-Queen Problem HC Multi Thread/"


# compiles
javac *.java

if [ $? -eq 0 ]
then
    echo "Compiled Successfully"
else
    echo "Failed to compile"
    exit 1
fi

# run many times
for ((i=0; i<= ($NUMBEROFRUNS-1); i++))
do
    multiThreadResult+=("$(java Main "$NUMBEROFQUEENS" | tail -n 1)")
    Multiaverage=$((Multiaverage + multiThreadResult[i])) #calculate average
    if [ $NUMBEROFQUEENS -gt 30 ] #show progress for lots of queens
    then
        echo "Running"
    fi

done

# actually calculate average
Multiaverage=$((Multiaverage / NUMBEROFRUNS))

##### OUTPUTS

echo
echo "------------------------------------------"
echo "For Single Threaded, average is: $average"
echo "Individual times are: ${singleThreadResult[*]}"
echo
echo "------------------------------------------"
echo
echo "For Multi Threaded, average is: $Multiaverage"
echo "Individual times are: ${multiThreadResult[*]}"
echo "------------------------------------------"

```