This visualization uses Leaflet and some awesome CartoDB dark tiles to show how concealed carry laws have changed over time. First thing is to create the dataset. This is done in data/data.csv just because it's easier to work with this sort of stuff in Excel when you're actually generating the data yourself. Then the data was converted from CSV to JSON using http://www.convertcsv.com/csv-to-json.htm. The data that's fed into the application comes from data/data.json, which has entries like this:

```
{
	"State":"Alaska",
	"1986":0,
	"1987":0,
	"1988":0,
	"1989":0,
	"1990":0,
	"1991":0,
	"1992":0,
	"1993":0,
	"1994":2,
	"1995":2,
	"1996":2,
	"1997":2,
	"1998":2,
	"1999":2,
	"2000":2,
	"2001":2,
	"2002":2,
	"2003":3,
	"2004":3,
	"2005":3,
	"2006":3,
	"2007":3,
	"2008":3,
	"2009":3,
	"2010":3,
	"2011":3,
	"2012":3,
	"2013":3,
	"2014":3,
	"2015":3
}
```

which designates that Alaska started as no-issue, moved to shall-issue in 1994, and changed to unrestricted carry in 2003 (there's a data dictionary within the Javascript code, but 0 = no issue, 1 = may issue, 2 = shall issue, and 3 = unrestricted carry). There's also a data/us-states.json file, which contains a GeoJSON of the state boundaries. The Javascript merges these two and colors the states within the GeoJSON depending on the status of the state in the given year. When the year changes, we tell Leaflet to recolor. Also, popups are generated in the beginning for each state by parsing the data/data.json file.

What I personally love about this site is that I can apply this code to whatever data I have really easily as long as I have state level data in the data/data.json format listed above. This code is less about the data and more about the fact that this is a super easy way to create a time lapse choropleth.

Source data is: http://upload.wikimedia.org/wikipedia/commons/a/a8/Rtc.gif and I also did research on my own to fill in the last few years.

I've also implemented Google Analytics and social media buttons. Please change out any app ID's in there if you fork, but please feel free to do whatever you want with this code.