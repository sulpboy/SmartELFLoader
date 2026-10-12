#Create 32-bit executable for fib.c

#Provide the command for cleanup

all: sum

sum: sum.c
	# 32-bit, no CRT/libc, entry=_start, non-PIE
	gcc -m32 -nostartfiles -nostdlib -no-pie -Wl,-e,_start -o sum sum.c

clean:
	rm -f sum
