# Arduino_RealTime_IIR
This library computes Infinite Impulse Response Filter. </br>
Filter coefficients, for example, could be evaluate in Matlab (R) and then passed as arguments in the IIR constructor method.
## Usage example
Arduino_RealTime_IIR is a library composed by one class: RT_IIR. </br>
RT_IIR class has a constructor and 3 methods. Uses of this library is very simple:
1. create an instance of RT_IIR object defining filter coefficients
2. filter each sample of your signal
### How to make a RT_IIR instance
To make a RT_IIR instance you need to declare a RT_IIR object and then pass the filter parameters to the constructor method:</br>
``` 
...
RT_IIR <T> iir = new RT_IIR(b, a, nb, na);
...
```
Where: b is an array (of type:T, eg: T = double or float) contains numerator coeffs, a is an array (of type:T) contains denominator coeffs, nb is the length of b array, na is the length of a array. </br>
RT_IIR is a template class, so you are allow to filter float or double (or other type) typed samples. 

### How to filter samples
To filter new sample acquired you have to call ``` iir.add(T sample) ``` method as follows: </br>
```
...
filteredSample = iir.add(sample);
...
```
``` iir.add(T sample) ``` add a new sample to the list of samples in processing and computes the filtering operation. This method return the result of the filtering operation. </br>
``` iir.compute() ``` return the result of filtering operation without any new sample added to the filtering samples queue. </br>
``` iir.getLastOutput() ``` return the value of the last result obtained by ```iir.add(T sample)``` or ```iir.compute()``` method.
