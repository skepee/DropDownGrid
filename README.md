# DropDownGrid
Jquery filtering elements in grid

When you have a grid with a lot of rows, this code helps you to filter dynamically and to highlight the values in grid you are looking for. In the link example below, by hovering in the header, a list of distinct values in the columns comes out. If you select one of these values, the row where corresponding value is present is highlighted.

Demo: https://codepen.io/skepee/pen/KYMVPZ


 $(".header").hover(function()
        {
            $(".row").removeClass("highlight");
            $(".dddown ul").empty();
            var uniqueVals=[];
            var index=$(this).index();
            var totElementsinRows=$(".rowelem").length;
            var totElements=$(".row:eq(1)").children().length;
            var rows=totElementsinRows/totElements;
           /* console.log("tot elements:" + totElementsinRows);
            console.log("tot elements in row:" +  totElements);
            console.log("tot rows:" +  rows);*/
            for(i=0;i<=rows-1;i++)
            {
                var ix=index+ i*totElements;
                var elem =$(".row .rowelem:eq(" + ix  + ")").html();
                uniqueVals.push("<li>" + elem + "</li>");
            }
            uniqueVals = jQuery.unique(uniqueVals.sort());            
            $(".dddown ul").append(uniqueVals);
            $(this).find(".dddown").toggle();
        });








![design](https://github.com/skepee/DropDownGrid/blob/master/DropDownValues.jpg)
