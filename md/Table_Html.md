# <font size="15" color="GREEN">Table </font>#
    一个 HTML 表格包括 <table> 元素，一个或多个 <tr>、<th> 以及 <td> 元素。
    
    <tr> 元素定义表格行，<th> 元素定义表头，<td> 元素定义表格单元。
## 属性 ##

<table  border="2" style="table-layout: fixed; width:100%;">

<th colspan="1" ><font size="14" color="GREEN" ,>属性</font></th>
<th colspan="1"><font size="14" color="GREEN" >值</font></th>

<tr>
    <td rowspan="3" >table-layout</td> 
	<td>属性用来显示表格单元格、行、列的算法规则</td>

</tr>
<tr>
<td>
固定表格布局：<font color="red">（table-layout: fixed）</font>
<br>
但是当设置了fixed属性的时候，如果表格设置了width属性height属性，如果设置的单元格宽高累加起来的总和比表格设置的宽高总和要大，那么表格的实际宽高就为每个单元格宽高累积的总和，但是如果单元格累积的总和比表格自己设计的要小，那么表格的宽高属性则为表格设置的宽高值。
</td>

</tr>

<tr>
<td>
自动表格布局：<font color="red">（table-layout: auto）</font>
</br>
当设置为auto属性，也就是table-layout属性的时候，如果表格设置了width属性height属性，那么表格的宽度和高度就是设置的值。不管你是否设置了单元格的高宽值，表格的高宽都已经限定了！如果没有设定，那么表格宽度高度则为单元格宽高（包括一些padding、border属性等）累积的总和。

</td>
</tr>



</table>