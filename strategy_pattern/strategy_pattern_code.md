# Strategy Pattern Code

Now Client wants to sort something. There are three strategys:

* Bubble Sort
* Insertion Sort
* Selection Sort

```
public interface Sort{
    public abstract int[] sort(int arr[]);
}
```


```
public class BubbleSort implements Sort{
    public int[] sort(int arr[]){
        // Bubble Sort
        return arr;
    }
}
```

```
public class InsertionSort implements Sort {
    public int[] sort(int arr[]) {
        // Insertion Sort
        return arr;
    }
}
```
```
public class SelectionSort implements Sort {
    public int[] sort(int arr[]) {
        // Selection Sort
        return arr;
    }
}
```

#### Context:

```
public class Handler
{
    private Sort sortObj;

    public int[] sort(int arr[])
    {
        sortObj.sort(arr);
        return arr;
    }

    public void setSortObj(Sort sortObj) {
        this.sortObj = sortObj;
    }
}
```

#### Client to test:

```
public class Client {

    public static void main(String args[]) {
       int arr[] = {1,4,6,2,5,3,7,10,9};
       int result[];
       Handler handler = new Handler();

       handler.setSortObj(new SelectionSort()); // Set one strategy
       result=ah.sort(arr);

       for(int i=0;i<result.length;i++) {
            System.out.print(result[i] + ",");
       }
    }
}
```
