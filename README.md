# LeetCode  Testtttt

***implementation by Swift*** 

## Product array 

> Given an array of n integers where n > 1, nums, return an array output such that output[i] is equal to the product of all the elements of nums except nums[I].
Solve it without division and in O(n). For example, given [1,2,3,4], return [24,12,8,6].

 [              1,         a[0],    a[0]*a[1],    a[0]*a[1]*a[2],  ]
     [ a[1]*a[2]*a[3],    a[2]*a[3],         a[3],                 1,  ]
     
 ```
    func productArray(inputArray: Array<Int>) -> Array<Int>  {
         guard !inputArray.isEmpty else {
            // throws
            return []
        }
            let arrayCount = inputArray.count
            var outPutArray = Array(repeating: 1, count: arrayCount)
            for n in 1...(arrayCount - 1) {
                outPutArray[n] = outPutArray[n - 1] * inputArray[n - 1]
            }
            var right = 1
            for n in 0...(arrayCount - 1) {
                let index = arrayCount - 1 - n
                outPutArray[index] *= right
                right *= inputArray[index]
            }
            debugPrint("inputArray ---- \(inputArray); outPutArray --- \(outPutArray);")
            return outPutArray
     }
```

## Number first
     
>Given an array nums, write a function to move all non-zero numbers to the head of it while maintaining the relative order of the non-zero numbers.
 For example, given nums = [0, 1, 0, 3, 12], after calling your function, nums should be [1, 3, 12, 0, 0].
 Note: You must do this in-place without making a copy of the array. Minimize the total number of operations.

```
    // MARK: - 2. Number first
    func NumberFirst(input: Array<Int>) -> Array<Int> {
        var inputArray = input
         guard !inputArray.isEmpty else {
            // throws
            return []
        }
        let arrayCount = inputArray.count
        var num = 0
        var zeroCount = 0
        for n in 0...(arrayCount - 1) {
            if inputArray[n] == 0 {
                zeroCount += 1;
            } else {
                inputArray[num] = inputArray[n]
                num += 1
            }
         }
        for _ in 0...(zeroCount - 1) {
            inputArray[num] = 0
            num += 1
        }
        debugPrint("NumberFirst ---- \(inputArray)")
        return inputArray
    }
```

## Power
   > Implement pow(x, n).
 
 ```
    func Power(num1:Double, num2:Int) -> Double {
        let x = num1
        var n = num2
        if x == 0 && n == 0 {
           // throws
            return 0
        }
        var isNegative = false
        if n < 0 {
            n *= -1
            isNegative = true
        }
        let result = pow(x: x, n: n)
        if isNegative {
            return 1.0 / result
        } else {
            return result
        }
    }
    
    func pow(x:Double, n:Int) -> Double {
        if n == 0 {
            return 1
        } else {
            let result = pow(x: x, n: n / 2)
            if n % 2 != 0 {
                return x * result * result
            } else {
                return result * result
            }
        }
    }
```
