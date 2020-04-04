all: c a m u
a: c
	clang -g -fsanitize=address *.c && ./a.out
m: c
	clang -g -fsanitize=memory *.c && ./a.out
u: c
	clang -g -fsanitize=undefined *.c && ./a.out
mike:
	cat *.c >> mike.c
ccomp: c mike
	ccomp -fstruct-passing mike.c && ./a.out
interp: c mike
	ccomp -interp -quiet -fstruct-passing mike.c
c:
	rm -rf *.o *.out mike.c
