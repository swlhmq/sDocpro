
df
===
df   

du
===
du   

find
===
find   

grep
===
grep   

ln
===
ln   

mount
===
mount   

unmount
===
unmount   

tar
===
GNU `tar' saves many files together into a single tape or disk archive, and can restore individual files from the archive.   

(1)-czf  
-c, --create  
-f, --file  
-z, --gzip
\# Create archive.tar from files or directories foo and bar.  
tar -cf archive.tar foo bar   
\# and zip the tar file with GNU zip   
tar -czf archive.tar.gz foo bar   
(2)-x  
-x, --extract  
\# Extract all files from archive.tar.  
tar -xf archive.tar   
(3)-p  
--preserve-permissions  
(4)-v  
--verbose   
verbosely list files processed   

