# **Minimum number of Operations to convert n to 1**

### Question : 
Given a single digit number, convert it to one either by:
    - Dividing it by a number
    - Subtracting it by 1
Return number of operations

### Java Solution(Using Recursion):
```java
class MinimumOpsToConvertNTo1 {
    public static void main(String[] args) {
        int ops = 0;
        int num = 1;
        makeOne(num,0);
    }
    
    static boolean isPrime(int n){
        if(n == 1){
            return true;
        }
        if(n>1){
            for(int i=2; i<=n/2; i++){
                if(n%i == 0){
                    return false;
                }
            }
        }
        return true;
    }
    static int gd(int n){
        int maxdiv = 1;
        for(int j = 2; j<n; j++){
            if(n%j == 0 ){
                maxdiv = j;
            }
        }
        return maxdiv;
    }
    static void makeOne(int n, int ops){
        if(n == 1){
            System.out.println(ops);
            return;
        }
        if (isPrime(n) == true){
            n = n-1;
            ops ++;
            makeOne(n,ops);
        }
        else if(gd(n) > 1){
            ops ++;
            n = n/gd(n);
            makeOne(n,ops);
        }
    }
}
```