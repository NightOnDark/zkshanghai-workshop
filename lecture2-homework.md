# 第2课 课后作业

## 第1题 xxxxxx
```
template Num2Bits(n) {
    signal input in;
    signal output bits[n];
    var z=0;
    var e2=1;
    for (var i = 0; i<n; i++) {
        bits[i] <-- (in >> i) & 1;
        bits[i] * (bits[i] -1 ) === 0;
        z += bits[i] * e2;
        e2 += e2;
    }

    z === in;
}
```

```
template IsZero() {
    signal input in;
    signal output out;

    signal inv;

    inv <-- in!=0 ? 1/in : 0;

    out <== -in*inv +1;

    in*out === 0;
}
```

```
template IsEqual() {
    signal input in[2];
    signal output out;
    signal ins;
    signal outs;
    
    signal inv;
    ins <== in[1] - in[0];
    inv <-- ins!=0 ? 1/ins : 0;
    outs <== -ins*inv +1;
    ins*outs === 0;
    out <== outs;
}
```

```
template IsNegative() {
    signal input in[254];
    signal output sign;

    component comp = CompConstant(10944121435919637611123202872628637544274182200208017171849102093287904247808);

    var i;

    for (i=0; i<254; i++) {
        comp.in[i] <== in[i];
    }

    sign <== comp.out;
}
```

```
template LessThan(n) {
    assert(n <= 252);
    signal input in[2];
    signal output out;

    component n2b = Num2Bits(n+1);

    n2b.in <== in[0]+ (1<<n) - in[1];

    out <== 1-n2b.out[n];
}
```

```
template Selector(choices) {
    signal input in[choices];
    signal input index;
    signal output out;
    component lessThan = LessThan(4);
    lessThan.in[0] <== index;
    lessThan.in[1] <== choices;
    lessThan.out === 1;
    signal ins[choices];
    signal oust;

    signal sums[choices];

  


   
    component eqs[choices];

  
    for (var i = 0; i < choices; i ++) {
        eqs[i] = IsEqual();
        eqs[i].in[0] <== i;
        eqs[i].in[1] <== index;
       
        ins[i] <== eqs[i].out * in[i];
    }   
    sums[0] <== ins[0];

    for (var i = 1; i < choices; i++) {
        sums[i] <== sums[i-1] + ins[i]
    }

    outs <== sums[choices-1];
    out <== outs;
}
```






