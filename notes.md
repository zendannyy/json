
## json structures

Fundamentally, json structures are made up of 3 components 

- Object 
- Array 
- Value 

Even though we mainly think of json as key Value pairs, this is Just the Object piece of the structure. 
The keys must be strings, the Values could be a multitide of data types.

### jq
A jq program is a "filter": it takes an input (valid json), and produces an output.
It supports the following filter logic 
- conditionals
- comparisons
- regex 

### Examples

- Simplest filter to run 
- ```jq '.' file.json```
#### This will return standard json output for the given input 
`
- Filter to access an array by value
-  ```jq '.key[2]' example.json```

- Filter to write output to std out, and a compact output by putting each JSON object on a single line
- ```jq -c 'select(.alert.severity==1)' eve.json | head -1 ```
```| jq -rc '.payload' | base64 -d && awk '{print $0}'   ```

- To iterate through files and "pretty print" them, creating a new file each time to differentiate. 
- ```for file in *.json; do jq '.' "$file" > "${file}_prettify"; done```


### References
- [JSON Standard](https://www.json.org/json-en.html)
- [JQ Man Page](https://linuxcommandlibrary.com/man/jq)
