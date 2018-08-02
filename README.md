# JavaScript-Interview-Question

## Question 1. K'th smallest element of an unsorted array. 

### Answer 
```
var findSmallest = (arr,k)=>{
   arr=arr.sort();
  return arr= k>0?arr[k-1]:"Value of k should be greater than 0"
}
```
## Question 2. K'th smallest element of a sorted rotated array.
### Answer 
```
var findMin = (arr,low,high,k)=>{
  if(high<low){
    return arr[0]
  }
  if(high == low){
   return arr[low];
  }
  let mid=Math.ceil(low+high/2);
  if(mid<high && arr[mid+1]<arr[mid]){
    return arr[mid+k];
  }
  if(mid>low && arr[mid] < arr[mid - 1]){
    return arr[mid+k];
  }
  if(arr[high]>arr[mid]){
    findMin(arr, low, mid-1,k);
  }else{
    findMin(arr, mid+1, high,k);
  }
  
}
```
## Question. 3 First unique character of a string.

### Answer 
```
let firstUniqChar=(input)=>{
  let obj={};
  input.split('').forEach(val=>{
   console.log(obj.hasOwnProperty(val));
    if(obj.hasOwnProperty(val)){
      obj[val]++;
    }else{
      obj[val]=0;
    }
    
  });
  
  
  for(let key in obj){
    if(obj[key]==0){
      return input.search(key);
    }
  }
  
}
```
