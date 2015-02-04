#bits - a simple api for working with bits

bits does the dirty, and extends JS built-ins

'''
> (0xa0a0).shift('>', 2)
          .drop(6, 12)
          .crop(4, 8)
          .bits()
'1010'
'''


## Getting started
$ node
> require('bits.js');

## Number conversion 
> (3).bits()
'11'

> (10).hex()
'a'

## Bit cropping
> (0xf0).bits()
'11110000'

> (0xf0).crop(4,8).bits()
'1111'

## Bit shifting
> (0xf).bits()
'1111'

> (0xf).shift('>', 1).bits()
'111'

Equivalent to '>>' operator
> (0xf >> 1)
'111'

> (0xffffffff).bits()
'11111111111111111111111111111111'

Overflow error
> (0xffffffff << 1)
-2

Tadahh!
> (0xffffffff).shift('<', 1).bits()
'111111111111111111111111111111110'

## Bit dropping
> (0xf0f).bits()
'111100001111'

> (0xf0f).drop(4, 8).bits()
'11111111'

## Bit masking
> (0xa0f).bits()
'101000001111'

Create a mask
> (0xa0f).mask(8, 12).bits()
'101000000000'

## Convenience methods
> (0xf).bits()
'1111'

> (0xf).even()
false

> (0xf).odd()
true

> (0xf).size()
4

Create a byte array!
> (0xffff).bits()
'1111111111111111'
> var bytes = (0xffff).toBytes()
> bytes.map(function(byte) { return byte.bits(); })
[ '11111111', '11111111' ]
