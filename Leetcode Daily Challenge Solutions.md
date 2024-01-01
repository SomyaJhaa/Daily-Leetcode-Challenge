# Leetcode Daily Challenge Solutions

This is my attemp to make the coding experience easir for you guys so that you can easily learn what to do in today's leetcode challenge.


## Preview 


## Todays 31-12-23
```
class Solution {
    public int maxLengthBetweenEqualCharacters(String s) {
        int msl = -1; // maximum substring length
        HashMap<Character, Integer> m = new HashMap<>();
        for( int i = 0; i < s.length(); i++){
            if( m.containsKey(s.charAt(i))){
                msl = Math.max( msl, i - m.get(s.charAt(i)));
            }
            else{
                m.put(s.charAt(i), i+1);
            }
        }
        return msl;
    }
}
```