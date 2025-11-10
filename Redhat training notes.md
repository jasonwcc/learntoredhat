RH134 Nov 2025
" " - display message, $^~? 
' ' - display everything literally
` ` - backtick. command substitution . Similar to $(cmd)

PS1 = prompt setting level 1
PS2 = prompt setting level 2
PS3 = select statement
PS4 = debug

Initialization file
/etc/profile  call /etc/bashrc

/etc/bashrc
var1=100
var2=200
var3=300

~/.bash_profile --> /bashrc
var1=111
var4=400

~/.bashrc
var1=1111
var5=500

variable="data"
alias="commands"

if a=100 and b=200
[ ]
[[ ]]
( )

case

for i in a b c d
do
 cmd1
 cmd2
done

while [while condition is still true ]
do
 cmd1
 cmd2
done

until  [while condition is still false]
do
 cmd1
 cmd2
done


noglob off ==> glob (enable * to be used as wildcard)
noglob on  ==> no glob (disable * as wildard)


