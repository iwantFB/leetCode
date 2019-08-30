```
    func longestMountain(_ A: [Int]) -> Int {
        
        guard A.count >= 3 else {
            return 0;
        }
        
        var longest = 0;
        var peak = [Int]();
        for i in 1 ..< A.count-1 {
            if A[i - 1] < A[i] && A[i] > A[i+1] {
                peak.append(i);
            }
        }
        
        for i in peak {
            var currentIndex = i;
            var tempCount = 1;
            while currentIndex - 1 >= 0 && A[currentIndex - 1] < A[currentIndex] {
                tempCount += 1;
                currentIndex -= 1;
            }
            
            currentIndex = i;
            while currentIndex + 1 < A.count && A[currentIndex] > A[currentIndex + 1] {
                tempCount += 1;
                currentIndex += 1;
            }
        
            
            longest = max(longest, tempCount);
        }

        return longest;
    }

```