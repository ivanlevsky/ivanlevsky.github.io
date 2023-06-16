```shell
#add "[[ -n ${line} ]]" read file last line
while read line || [[ -n ${line} ]];do
#",,"to lowercase, "^^"to uppercase,"*"abc"*" search text contains abc
if [[ ${line,,} == *"abc"* ]]; then
#split line text to array with ","
   IFS="," read -a myarray <<< $line;
   echo ${myarray[1]}
fi
done <text.csv
```
