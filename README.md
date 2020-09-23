<div align="center">

## Week Select on Calendar


</div>

### Description

Always select a week on the calendar control on your ASP.net Page. Make sure when using this code you change the SelectionMode of your Calendar control to DayWeek.

All you need to do is call this code from the SelectionChanged event of your calendar control.
 
### More Info
 
System.Web.UI.WebControls.Calendar myControl

Change the SelectionMode of your Calendar control to DayWeek.

In the SelectionChanged event of your calendar control call this code passing in calendar control (you will need to cast it from an object)

Example:

CalendarSelectWeek((Calendar) sender);


<span>             |<span>
---                |---
**Submitted On**   |
**By**             |[Doug Cameron](https://github.com/Planet-Source-Code/PSCIndex/blob/master/ByAuthor/doug-cameron.md)
**Level**          |Intermediate
**User Rating**    |5.0 (15 globes from 3 users)
**Compatibility**  |C\#, ASP\.NET
**Category**       |[Controls/ Forms/ Dialogs/ Menus](https://github.com/Planet-Source-Code/PSCIndex/blob/master/ByCategory/controls-forms-dialogs-menus__10-3.md)
**World**          |[\.Net \(C\#, VB\.net\)](https://github.com/Planet-Source-Code/PSCIndex/blob/master/ByWorld/net-c-vb-net.md)
**Archive File**   |[](https://github.com/Planet-Source-Code/doug-cameron-week-select-on-calendar__10-1073/archive/master.zip)

### API Declarations

I have quickly tested this and it appears to work, this code didn't take long so please make sure you are happy with it before you use it for anything critical. Please leave any comments if you wish.


### Source Code

```
public static void CalendarSelectWeek(System.Web.UI.WebControls.Calendar myControl)
{
if (myControl.SelectedDates.Count == 1)
 // the user has only selected the day, need to select the week that day is in
 {
 System.DateTime tmpDate = myControl.SelectedDate;
 DayOfWeek myFirstDayOfWeek;
 //if the first day of week for calendar control is default, then that's not a day so change it to monday
 if (myControl.FirstDayOfWeek == System.Web.UI.WebControls.FirstDayOfWeek.Default)
 {
 myFirstDayOfWeek = (DayOfWeek) System.Web.UI.WebControls.FirstDayOfWeek.Monday;
 }
 else
 {
 myFirstDayOfWeek = (DayOfWeek) myControl.FirstDayOfWeek;
 }
 //loop back till we have the first day of the week
 while (myFirstDayOfWeek != tmpDate.DayOfWeek)
 {
 tmpDate = tmpDate.AddDays(-1);
 }
 myControl.SelectedDates.Clear();
 //go through the week adding it to the selected dates
 for (int i = 0; i <= 6; i++)
 {
 myControl.SelectedDates.Add(tmpDate.AddDays(i));
 }
 }
}
```

