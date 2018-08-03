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
## Question. 4 Minimum distance between 2 words counting the number of characters from middle of both words.
  - * Allow multiple separators in the split(Example: split(/[\s.,]/) )
  - *  Account for the split char in the total length between words (i.e. index += word.length() + 1 )
  - *  Allow for words in either order (Math.abs(word1Loc - word2Loc))
  - *  Handle case where either word is not present
### Answer
```
let findMinimumDistance= (str,w1,w2)=>{
let len1=w1.length,
    len2=w2.length,
    posW1=null,
    posW2=null,
    wlen= (len1+len2)/2,
   arr=str.split(/[\s,.]/);
  if(arr.includes(w1) && arr.includes(w2)){
    
    for(let val in arr){
       if(arr[val] === w1){
          posW1=val; 
       }
      if(arr[val] === w2){
        posW2=val;
       }
  
    }
    let i = posW1<posW2 ? posW1 : posW2,
       dist=0;
    i=1+Number(i);
   for(i;i<(posW1>posW2?posW1:posW2);i++){
     dist+= arr[i].length;
   } 
    return dist+Math.abs(posW1-posW2)+wlen;
  }

 return -1;
    
}
```
