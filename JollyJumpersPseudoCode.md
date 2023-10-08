while (there are more lines of input)
    read n from input
    set isJolly to true
    set differencesPresent to a boolean array of size n-1, initialized to false
    read first element as prev

    for i from 2 to n
        read current element as current
        calculate absolute difference as diff = abs(current - prev)
        
        if diff < 1 or diff > n - 1
            set isJolly to false
            break
        
        set differencesPresent[diff - 1] to true
        set prev to current
    
    if isJolly is true
        for each difference in differencesPresent
            if difference is false
                set isJolly to false
                break

    output "Jolly" if isJolly is true, otherwise "not jolly"
