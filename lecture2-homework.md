# 第2课 课后作业

## 第1题 转换为bit位 Num2Bits
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
## 第2题 判零 IsZero
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
## 第3题 相等 IsEqual
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
## 第4题 选择器 Selector

## 第5题 判负 IsNegative
```
template CompConstant(ct) {
    signal input in[254];
    signal output out;

    signal parts[127];
    signal sout;

    var clsb;
    var cmsb;
    var slsb;
    var smsb;
    var sum=0;
    var b = (1 << 128) -1;
    var a = 1;
    var e = 1;
    var i;
    for (i=0;i<127; i++) {
        clsb = (ct >> (i*2)) & 1;
        cmsb = (ct >> (i*2+1)) & 1;
        slsb = in[i*2];
        smsb = in[i*2+1];

        if ((cmsb==0)&&(clsb==0)) {
            parts[i] <== -b*smsb*slsb + b*smsb + b*slsb;
        } else if ((cmsb==0)&&(clsb==1)) {
            parts[i] <== a*smsb*slsb - a*slsb + b*smsb - a*smsb + a;
        } else if ((cmsb==1)&&(clsb==0)) {
            parts[i] <== b*smsb*slsb - a*smsb + a;
        } else {
            parts[i] <== -a*smsb*slsb + a;
        }
        sum = sum + parts[i];
        b = b -e;
        a = a +e;
        e = e*2;
    }
    sout <== sum;
    component num2bits = Num2Bits(135);
    num2bits.in <== sout;
    out <== num2bits.out[127];
}

template IsNegative() {
    signal input in[254];
    signal output out;

    component comp = CompConstant(10944121435919637611123202872628637544274182200208017171849102093287904247808);

    var i;

    for (i=0; i<254; i++) {
        comp.in[i] <== in[i];
    }

    out <== comp.out;
}

```
## 第6题 少于 LessThan
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
## 第7题 整数除法 IntegerDivide
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






