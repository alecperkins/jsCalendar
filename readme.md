jsCalendar is a lightweight date picker for desktop and mobile browsers.

# Features

* small file size
* designed for webkit mobile, mainly iOS and Android
* support for desktop browsers
* works with jQuery as well as Zepto.js
* range of days selection mode
* single date selection mode
* 3D calendar turn over css3 animation, supported by Safari only
* multilingual support
* multiple calendars on one page possible
* selecting past dates is prevented

# Requirements

* [jQuery](http://jquery.com/) or [Zepto.js](https://github.com/madrobby/zepto)
* [Modernizr](http://www.modernizr.com/) or the included Modernizr custom build using a reduced subset

# Usage

On document ready, the calendar attaches itself to HTML elements with the class name "jsCalendar". Manual initialization is not necessary. This element should have an attribute `data-localized_date` with a JSON string as value containing the localized names of months and weekdays like this one:
    {"days":{"names":{"min":["Sun","Mon","Tue","Wed","Thu","Fri","Sat"]}},"months":{"names":{"long":["January","February","March","April","May","June","July","August","September","October","November","December"]}}}
    
It is possible to select a range of days between start and end date as well as selecting a single date. Range selection is default. To switch to single date selection, add the class name `jsSingleDate` to the jsCalendar HTML element before document ready.

You are notified when the user changes the selection by the custom events `startDateChanged` and `endDateChanged` on the jsCalender HTML element. So the currently selected dates can be retrieved like this:

    $(".jsCalendar").bind("startDateChanged", function() {
        $(this).data("startdate");
    }).bind("endDateChanged", function() {
        $(this).data("enddate");
    });

If you are using the single date selection mode, `startDateChanged` is the only triggered event.

To reset the selection programatically (e.g. with an extra button), you could trigger a `resetSelection` event on the jsCalender HTML element.

From the user's perspective, range selection works like this: the first click is the start date, second click the end date, a third click resets the selection.
If the selected end date is before the start date, they are automatically exchanged. It is possible to deselect a start or end date by clicking it without resetting the whole selection.

Your can implement your own date selection algorithm by rewriting the `dateSelected` method.

Right now, it is not possible to select a date in the past, there is no maximum selection date for the far future and it is not possible to define the first day of the week.

After initialization, the JavaScript Date object will be extended with a subset of instance methods from [datejs](http://www.datejs.com/): `clone`, `isLeapYear`, `getDaysInMonth`, `moveToFirstDayOfMonth`, `moveToLastDayOfMonth`, `addMilliseconds`, `addDays`, `addMonths` and `clearTime`.

The `$` function is extended with a `slice` method to select a range from a set of elements like this `$("a").slice(3, 7)`, using the native slice implementation for arrays.

# Example

See index.html

# Supported Platforms

* tested with Zepto.js:
  * Android
  * iOS
  * Safari
  * Chrome
* tested with jQuery
  * Android
  * iOS
  * Safari
  * Chrome
  * Firefox
  * Internet Explorer 7

# License

jsCalendar is licensed under the terms of the MIT License.