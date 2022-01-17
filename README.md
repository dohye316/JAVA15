# JAVA15
Arrays类和内部类
Aarrays类
Arrays类常见方法应用案例
Arrays里面包含了一系列静态方法，用于管理或操作数组（比如排序和搜索）
1.toString 返回数组的字符串形式
Arrays.toString(arr)
2.sort排序（自然排序和定制排序）Integer arr[]={1,-1,7,0,89}
3.binarySearch 通过二分搜索法进行查找，要求必须排好序
int index = Arrays.binarySearch(arr,3))
binarysort二叉树排序
在binarySort方法底层，会通过匿名内部类的compare方法来决定排序的顺序

==========================================

public class ArraysMethod01 {
    public static void main(String[] args) {
        Integer[]integers = {1,20,90};
        //遍历数组
        //for(int i =0; i <integers.length;i++){
//        System.out.println(integers[i]);}
        System.out.println(Arrays.toString(integers));
        //演示sort方法的使用
        Integer arr[]={1,-1,7,0,89};


        for (int i = 0; i <arr.length;i++) {
            System.out.print(arr[i]);
        }
        System.out.println("");
        //进行排序
        //老韩解读
        //1.可以直接使用冒泡排序，也可以使用Arrayss提供的sort
        //2.因为数组是引用类型，所以通过sort排序后，会直接影响到实参arr
        //3.sort重载的，也可以通过传入一个接口 Comparator 实现定制排序
        //4.调用 定制排序时，传入两个参数（1）排序的数组arr
        //5.看效果
        //6.这里体现了接口编程的方式，看看源码，就明白
        // (2)实现了Comparator接口的匿名内部类，要求实现compare方法
        //定制排序
        //Arrays.sort(arr);//默认排序方法
//       底层调用了这个方法
        //(1)Arrays.ort(arr,new Comparator())
        //(2)最终到TimSort类的 private static<T>void binarySort(T[]a,int lo,
        // Comparator<? super T>c )()方法的代码
        //(3)执行到binarySort方法的代码，
//       while (left < right) {
//            int mid = (left + right) >>> 1;
//            if (c.compare(pivot, a[mid]) < 0)//影响排序顺序
//                right = mid;
//            else//在binarySort方法底层，会通过匿名内部类的compare方法来决定排序的顺序
//                left = mid + 1;
//        }
//（4） new Comparator(){
//        @Override
//        public int compare(Object o1, Object o2) {
//            Integer i1 = (Integer)o1;
//            Integer i2 = (Integer)o2;
//
//
//
//            return i2-i1;
//        }
        //(5)public int compare(Object o1,Object o2)返回的值>0还是<0
        //会影响整个排序的结果，这就充分体现了， 接口编程+动态绑定+匿名内部类的综合使用
        //将来的底层框架和原码的使用，使用方式，会非常常见
        //Arrays.sort(arr)

        Arrays.sort(arr,new Comparator(){
            @Override
            public int compare(Object o1, Object o2) {
                Integer i1 = (Integer)o1;
                Integer i2 = (Integer)o2;



                return i2-i1;
            } //这是内部类
        });
        System.out.println("===排序后===");
        Arrays.sort(arr);
        System.out.println("排序后");
        System.out.println( Arrays.toString(arr));
    }
}
Arrays里面包含了一系列静态方法，用于管理或操作数组（比如排序和搜索）
1.toString 返回数组的字符串形式
Arrays.toString（arr）
2.sort排序（自然排序和定制排序） Integer arr[]={1,-1,7,0,89}
ArraysSortCustom.java
3.binarySearch 通过二分搜索法进行查找，要求必须排序好序
int index = Arrays.binarySearch(arr,3);




import java.util.Arrays;
import java.util.Comparator;

/**
 * @author 郑道炫
 * @version 1.0
 */
public class ArraysSortCustom {
    public static void main(String[] args) {
        int[]arr ={1,-1,8,0,20};
           bubble02(arr, new Comparator() {
               @Override
               public int compare(Object o1, Object o2) {
               int i1 = (Integer)o1;
               int i2 = (Integer)o2;
               return  i2 -i1;//retur i2 - i1;
               }
           });
        System.out.println("定制排序");
        System.out.println(Arrays.toString(arr));

    }
    //实用冒泡排序

    public static void bubble01(int[]arr){
        int temp =0;
        for (int i = 0; i < arr.length-1; i++) {
            for (int j = 0; j < arr.length -1-i; j++) {
                if (arr[j] >arr[i+1]){
                    temp = arr[i+1];
                    arr[j] = arr[j+1];
                    arr[j+1] = temp;
                }//从大到小
            }
        }
    }//进行改进
    //结合冒泡+定制排序
    public static void  bubble02(int[]arr, Comparator c){
        int temp =0;
        for (int i = 0; i < arr.length-1; i++) {
            for (int j = 0; j < arr.length -1-i; j++) {
                if (c.compare(arr[j],arr[j+1])>0){
                    temp = arr[j];
                    arr[j] = arr[j+1];
                    arr[j+1] = temp;
                }//从大到小
            }
        }
    }
    }


Arrays类常见方法应用案例
Arrays里面包含了一系列静态方法，用于管理或操作数组（比如排序和搜索）。
1.toString 返回数组的字符串形式
Arrays.toString(arr)
2.sort排序（自然排序和定制排序）Integer arr[]={1,-1,7,0,89}
3.binarySearch 通过二分搜索法进行查找，要求必须排好序
int index = Arrays.binarySearch(arr,3);







