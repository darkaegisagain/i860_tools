# i860_tools

Last known version of the gnu binutils and gcc to compile the

Instructions building


../binutils-2.14/configure --target=i860-stardent-sysv4 --prefix=/opt/i860 --disable-multilib
make
make install

(there are probably later ones that still have the right support. I didn't look too hard)

Ensure the resulting i860 directory is on your path

edit gcc/config/i860/i860.md
go to line 1229

Comment out the stanza

#;; AC
#;;(define_insn ""
#;; [(set (match_operand:QI 0 "register_operand" "=r")
#;; (match_operand:QI 1 "indexed_operand" "m")Wink]
#;; ""
#;; "ld.b %1,%0")

which appears to be a bug that never got fixed upstream

../gcc-3.4.6/configure --target=i860-stardent-sysv4 --prefix=/opt/i860 --disable-multilib --disable-threads --enable-languages=c --disable-shared --without-headers --disable-libssp --disable-libmpx --disable-libatomic
make
make install

