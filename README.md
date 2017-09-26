# perl5-benchmark

simple benchmark files for Porting/bench.pl

Porting/bench.pl tool from Dave Mitchell

http://www.nntp.perl.org/group/perl.perl5.porters/2014/11/msg222802.html
http://blogs.perl.org/users/rurban/2015/01/new-perl5-portingbenchpl.html


Samples from: https://rt.perl.org/Public/Bug/Display.html?id=129990

Benchmark two different perl
```
./perl -Ilib Porting/bench.pl --benchfile=../129990-bench ../perl2/perl=blead ./perl=blead+patch
```

with the file ../129990-bench containing this 
```
# ……………….……………….……………….……………….
[
 'package::simple' =>
 {
  desc => "simple one-word package name",
  setup => 'sub foo {}',
  code => "&{'foo'}"
 },
 'package::quote' =>
 {
  desc => "multi-part package name using single quotes",
  setup => "sub xx'yy'zz'aa'bb'cc'foo {}",
  code => qq(&{"xx'yy'zz'aa'bb'cc'foo"})
 },
 'package::colon' =>
 {
  desc => "multi-part package name using colons",
  setup => "sub xx::yy::zz::aa::bb::cc::foo {}",
  code => "&{'xx::yy::zz::aa::bb::cc::foo'}"
 },
]
# ……………….……………….……………….……………….
```
