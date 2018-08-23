# Data-Structures-3-Array-List
import java.util.Arrays;
public class ArrayList implements List{
private int[] data;
private int size;

public ArrayList(){
data=new int[10];
size=0;
}
public int size(){
return size;
}
public void add(int value){
if(resize()) doubleSize();
data[size]=value;
size++;
}
public void compress(int a){
int count;
if(size%a==0) count=size/a;
else count=size/a+1;

for(int i=0; i<count; i++){
int sum=0;
 for(int j=a*i; j<a*i+a; j++){
 sum+=data[j];
  }
 data[i]=sum;
 }
  size=count;
}
public void add(int index,int value){
if(index<0 || index>size) throw new IllegalArgumentException();
for(int i=size; i>index; i--){
data[i]=data[i-1];
}
data[index]=value;
size++;
}
public int remove(int index){
int result=data[index];
for(int j=index; j<size-1; j++){
data[j]=data[j+1];
}
size--;
return result;
}
public int get(int index){
return data[index];
}
public boolean isEmpty(){
return size==0;
}
public void clear(){
data=new int[10];
size=0;
}
public void set(int index,int value){
data[index]=value;
}
public String toString(){
if(size==0) return "[]";
String result="[";
result+=data[0];
for(int k=1; k<size; k++){
result+=","+data[k];
 }
return result+"]";
}
private boolean resize(){
return size==data.length;
}
private void doubleSize(){
data=Arrays.copyOf(data,data.length*2);
}
public boolean contains(int num){
return indexOf(num)>0;
}
public int indexOf(int num){
for(int i=0; i<size; i++){
if(data[i]==num) return i;
}
return -1;
}
public void mergeSort(){
data=Arrays.copyOfRange(data,0,size);
mergeSort(data);
}
private void mergeSort(int[] data){
if(data.length>=2){
int[] array1=Arrays.copyOfRange(data,0,data.length/2);
int[] array2=Arrays.copyOfRange(data,data.length/2,data.length);

mergeSort(array1);
mergeSort(array2);
merge(data,array1,array2);
}
}
private void merge(int[] data,int[] array1,int[] array2){
int index1=0;
int index2=0;
for(int i=0; i<data.length; i++){
if(index1>=array1.length || (index2<array2.length && array2[index2]<array1[index1])){
data[i]=array2[index2];
index2++;
}else{
data[i]=array1[index1];
index1++;
  }
 }
}
}
