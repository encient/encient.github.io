*Format cell*

## Description
I heard there are hidden information here, can you find it for me?

Attachment: `challenge.xlsx`

## Solution
![](office-1.png)
///caption
///
The given tab in the excel sheet does not give us any useful information. We can try to search for hidden tabs.

![](office-2.png)
///caption
///
In Hidden3 tab, we will see that there are hidden texts in the cells. Changing the font colour or the fill colour will not help in revealing the text.

![](office-3.png)
///caption
///
Therefore, we can select all cells to change the format of the cells.

![](office-4.png)
///caption
///
Change the format to text so that the hidden text will be visible.

![](office-5.png)
///caption
///
Once the hidden texts are shown, we can kind of see that it is a QR code. We can apply rules to the cells so that it will fill with colour automatically.

![](office-6.png)
///caption
///
Image above shows the rules set by us to colour the cell.

![](office-7.png)
///caption
///
Once the new rule is applied, a clear QR code will be shown and it will redirect us to the flag.

## Flag
`GCTF2023{F0rmatt1ng_c311s_t0_h1d3_inf0rm4t10n}`