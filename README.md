# Bash-Script-Automation

rhyme@ip-172-31-148-150:~$ vim first.sh
rhyme@ip-172-31-148-150:~$ ls
----------------------------------------------------|
in script	(with enter of i)						|	
#!/bin/bash											|
echo this is our first script						|
													|
													|
													|
esc+ :wq for save									|
----------------------------------------------------|
Desktop    Downloads  Pictures  R          Videos       first.sh   snap
Documents  Music      Public    Templates  finished_ex  samplelog
rhyme@ip-172-31-148-150:~$ chmod +x first.sh
rhyme@ip-172-31-148-150:~$ ls
Desktop    Downloads  Pictures  R          Videos       first.sh   snap
Documents  Music      Public    Templates  finished_ex  samplelog
rhyme@ip-172-31-148-150:~$ ./first.sh
this is our first script
rhyme@ip-172-31-148-150:~$ ^C
rhyme@ip-172-31-148-150:~$ 


pwd: print working directory
ls : list files
man ls : manual list

rhyme@ip-172-31-148-150:~$ mkdir test
rhyme@ip-172-31-148-150:~$ cd test

rhyme@ip-172-31-148-150:~$ rm -r test


*****A Script to create Scripts *******
----------------------------------------------------|
in script	(with enter of i)						|	
#!/bin/bash											|
FILENAME=$1.sh
echo "#!/bin/bash" > $FILENAME
chmod +x $FILENAME
vim $FILENAME

					|
													|
													|
													|
esc+ :wq for save									|
----------------------------------------------------|
rhyme@ip-172-31-148-150:~$ vim cr.sh
rhyme@ip-172-31-148-150:~$ chmod +x cr.sh
rhyme@ip-172-31-148-150:~$ ls
rhyme@ip-172-31-148-150:~$ ./cr.sh hello
rhyme@ip-172-31-148-150:~$ ls
Desktop    Downloads  Pictures  R          Videos  finished_ex  hello.sh   snap
Documents  Music      Public    Templates  cr.sh   first.sh     samplelog
rhyme@ip-172-31-148-150:~$ 





----------------------------------------------------|
in script	(with enter of i)						|	
#!/bin/bash											|


FILENAME=$1.sh

if [[ -e $FILENAME ]]
then
        echo -n file already exists, are you sure you would like to overwrite? (y/n)
        read ANSWER
        case $ANSWER in
                y|Y|[yYi][eE][sS])
                        echo "#!/bin/bash" > $FILENAME
                        chmod +x $FILENAME
                        vim $FILENAME
                        ;;
                n|N|[nN][oO])
                        read -p "enter the new filename" FILENAME
                        FILENAME=$FILENAME.sh
                        ;;
        esac
fi

echo "#!/bin/bash" > $FILENAME
chmod +x $FILENAME
vim $FILENAME

													|
													|
esc+ :wq for save									|
----------------------------------------------------|
#!/bin/bash											|
													|


FILENAME=$1.sh

while [[ -e $FILENAME ]]
do
        echo -n "file exists already, are you sure would like to overwrite? (y/n)"
        read ANSWER
        case $ANSWER in
                y|Y|[yY][eE][sS])
                        break
                        ;;
                n|N|[nN][oO])
                        read -p "enter the new filename" FILENAME
                        FILENAME= $FILENAME.sh
                        ;;
         esac
 done





													|
													|
esc+ :wq for save									|
----------------------------------------------------|


*****A Script to create Scripts *******
----------------------------------------------------|
													|
													|
#!/bin/bash

SEARC_DIR=/home/ryhme/Downloads

find $SEARCH_DIR -mtime -1 -type f -iname "*.txt"


~   :wq
rhyme@ip-172-31-148-150:~$ ./findrecent.sh
./Downloads/file2.txt
./Downloads/file1.txt


#!/bin/bash

SEARC_DIR=/home/ryhme/Downloads

mkdir -p found
find $SEARCH_DIR -mtime -1 -type f -iname "*.txt" | xargs -I % cp % /home/rhyme/found




													|
													|
esc+ :wq for save									|
----------------------------------------------------|


*****A Script that parses log files*******
----------------------------------------------------|
													|
													|
#!/bin/bash

LOGFILE=samplelog

while read -r line;
do
		component=$(awk{'print $5'} | cut -d : -f 1)
		echo -e "$component\n" >> comp_errors 
done <<(grep -i "error" $LOGFILE)




