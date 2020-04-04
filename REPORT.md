Raw list of findings.
```
clang -g -fsanitize=memory *.c && ./a.out
==61800==WARNING: MemorySanitizer: use-of-uninitialized-value
    #0 0x5600d9c7669f in crypto_sign_ed25519_tinynacl_open /home/mpech/tinyssh-audit/ed25519/crypto_sign_ed25519.c:59:9
    #1 0x5600d9c7836e in test_precomp /home/mpech/tinyssh-audit/ed25519/crypto_sign_ed25519test.c:57:13
    #2 0x5600d9c77cd1 in main /home/mpech/tinyssh-audit/ed25519/crypto_sign_ed25519test.c:123:5
    #3 0x7fef2a19b022 in __libc_start_main (/usr/lib/libc.so.6+0x27022)
    #4 0x5600d9bf70ad in _start (/home/mpech/tinyssh-audit/ed25519/a.out+0x1f0ad)

SUMMARY: MemorySanitizer: use-of-uninitialized-value /home/mpech/tinyssh-audit/ed25519/crypto_sign_ed25519.c:59:9 in crypto_sign_ed25519_tinynacl_open
Exiting
```

```
$ tis-interpreter.sh ed25519/*.c
[value] Analyzing a complete application starting at main
[value] Computing initial state
[value] Initial state computed
ed25519/sc25519.c:23:[kernel] warning: invalid LHS operand for left shift. assert 0 ≤ carry;
                  stack: modL :: ed25519/sc25519.c:47 <-
                         sc25519_reduce :: ed25519/crypto_sign_ed25519.c:29 <-
                         crypto_sign_ed25519_tinynacl :: ed25519/crypto_sign_ed25519test.c:55 <-
                         test_precomp :: ed25519/crypto_sign_ed25519test.c:123 <-
                         main
[value] Stopping at nth alarm
[value] user error: Degeneration occurred:
                    results are not correct for lines of code that can be reached from the degeneration point.
```
