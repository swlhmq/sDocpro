
gnu-doc reference
===
http://www.gnu.org/software/bash/manual/

the entire command line
===
#!/bin/bash

variable
===
${variable_name}

skill="Java"   
echo "I am good at ${skill}Script"

if
===
The syntax of the if command is:   
if test-commands; then   
consequent-commands;   
[elif more-test-commands; then   
more-consequents;]   
[else alternate-consequents;]   
fi    

for example


for
===
The syntax of the for command is:   
for name [ [in [words ...] ] ; ] do commands; done   

An alternate form of the for command is also supported:   
for (( expr1 ; expr2 ; expr3 )) ; do commands ; done   

list="rootfs usr data data2"  
for i in $list;  
do  
echo $i is appoint;   
done

while
===
The syntax of the while command is:   
while test-commands; do consequent-commands; done   

while   



