# DropDownGrid
Jquery filtering elements in grid

When you have a grid with a lot of rows, this code helps you to filter dynamically and to highlight the values in grid you are looking for. In the link example below, by hovering in the header, a list of distinct values in the columns comes out. If you select one of these values, the row where corresponding value is present is highlighted.

Demo: https://codepen.io/skepee/pen/ROgewe


Basic function:
```
		function distinct(columnHover)
		{
			var valT=[];
			var valN=[];
			var elementsInColumn=[];
			totElementsinRows=$(".rowelem").length;
			totElements=$(".header").length;
			rows=totElementsinRows/totElements;
			
			for(i=0;i<=rows-1;i++)
			{
				var ix=columnHover+ i*totElements;
				var elem =$(".rowelem:eq(" + ix  + ")").text();				
				elementsInColumn.push(elem);
				
				var elemNum=parseFloat(elem);
				
				if (isNaN(elemNum))
				{
					if($.inArray(elem, valT) == -1)	
					{			
						valT.push(elem);
					}
				}
				else
				{
					if($.inArray(elemNum, valN) == -1)	
					{			
						valN.push(elemNum);
					}
				}
			}
					
			valN.sort(function compareNumbers(a, b) {
				  return a - b;
				});
				
			valT.sort();
						
			$.each(valT, function(index)
			{
				var val=valT[index];
				var badge=fbadge(elementsInColumn, val);
				
				if (val.trim()==="")
				{
					valT[index]="<li class='list-group-item'><i><span>null</span>" +  badge  + "</i></li>";
				}
				else
				{
					valT[index]="<li class='list-group-item'><span>" + valT[index] + "</span>" + badge +"</li>";
				}		
			});
			
			$.each(valN, function(index)
			{
				var badge=fbadge(elementsInColumn, valN[index]);
				valN[index]="<li class='list-group-item'>"  + "<span>" + valN[index] + "</span>"  + badge  + "</li>";			
			});
			
			return $.merge(valN,valT);
		}
```



![design](https://github.com/skepee/DropDownGrid/blob/master/DropDownValues.jpg)
