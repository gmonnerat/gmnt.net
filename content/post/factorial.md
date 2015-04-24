+++
categories = []
date = "2015-04-20T23:46:06+02:00"
description = ""
tags = ["Go"]
title = "Calculating factorial in Go"

+++

Calculate factorial in Go is simple. But, when you have big numbers, for
example 100!, [int64](http://golang.org/pkg/builtin/#int64) is not enough.

Then, I used [math/big](http://golang.org/pkg/math/big/) to calculate it.

    package main

    import "fmt"
    import "math/big"

    func factorial(x *big.Int) *big.Int {
      if x.Cmp(big.NewInt(0)) == 0 {
        return big.NewInt(1)
      }
      return big.NewInt(0).Mul(x,
        factorial(big.NewInt(0).Sub(x, big.NewInt(1))))
    }

    func main() {
      fmt.Println(factorial(big.NewInt(100)))
    }

The result to 100! is:
9332621544394415268169923885626670049071596826438162146859296389521
7599993229915608941463976156518286253697920827223758251185210916864
000000000000000000000000

This code is just an idea, probably can be simplified. Feel free to simplify
and share with me :).
