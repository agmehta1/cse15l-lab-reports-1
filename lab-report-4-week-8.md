# Week 8 Lab Report 4
## This lab report tests the code of our group and the group that we reviewed Week 7

* In this report I will be using [the CommonMark demo site](https://spec.commonmark.org/dingus/) as a reference for the expected output of each test snippet. 

### Snippet 1

```
`[a link`](url.com)

[another link](`google.com)`

[`cod[e`](google.com)

[`code]`](ucsd.edu)
```

* Expected output should include ```"`google.com"```, ```"google.com"```, and ```"ucsd.edu"```. [Reference](https://spec.commonmark.org/dingus/)

* For our implementation, the test did not pass. Below is the failing JUnit output.

![Image](lab-report-4-ss/Us_snip1.png)

* For the implementation we reviewed, the test also did not pass. Below is the failing JUnit output.

![Image](lab-report-4-ss/Them_snip1.png)

* For our implementation, I do not believe that there is a small code change that would make our program work. I think we would have to add a check if there is a ```"`"``` character between the `"["` and `"]"`. If there is, we would have to check any other ```"`"``` character to determine their pairing. Only if the ```"`"``` inside the square brackets is not in a pair with a another ```"`"``` outside of the two square brackets will the link be added to the return arraylist.