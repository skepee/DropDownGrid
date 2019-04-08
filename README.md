# DropDownGrid
Jquery filtering elements in grid

When you have a grid with a lot of rows, this code helps you to filter dynamically and to highlight the values in grid you are looking for. In the link example below, by hovering in the header, a list of distinct values in the columns comes out. If you select one of these values, the row where corresponding value is present is highlighted.

Demo: https://codepen.io/skepee/pen/KYMVPZ


Basic function:
```
 $(".header").hover(function()
   {
       $(".row").removeClass("highlight");
       $(".dddown ul").empty();
       var uniqueVals=[];
       
       // get the index of selected column when you hover on the header
       var index=$(this).index();
       
       // get the total elements in the grid (not considering the header elements)
       var totElementsinRows=$(".rowelem").length;
       
       // get the number of columns
       var totElements=$(".row:eq(1)").children().length;
       
       // calculates the number of rows.
       var rows=totElementsinRows/totElements;

       for(i=0;i<=rows-1;i++)
       {
           // get the position of data in the array
           var ix=index+ i*totElements;
           
           // get the content value in that position
           var elem =$(".row .rowelem:eq(" + ix  + ")").html();
                      
           uniqueVals.push("<li>" + elem + "</li>");
       }
       
       // once all values are pushed in a temporary array, the array is sorted and then the unique values can be achieved.
       uniqueVals = jQuery.unique(uniqueVals.sort());            
       
       // the elements list is appended to the dynamic droppdown.
       $(".dddown ul").append(uniqueVals);
       $(this).find(".dddown").toggle();
   });
```



![design](https://github.com/skepee/DropDownGrid/blob/master/DropDownValues.jpg)
