Show a map with mapbox with photo published in your Koken
============

First, be aware that i am not a all a javascript developer, neither for koken. I am sure that the script can be corrected / optimized.
Do not hesitate if you have suggestion.

## How to install it :
- Download the file called map.lens
- First create an account on MapBox.com
- Create a project, it will give you a "Map ID"
- Add it to map.lens : var map = L.mapbox.map('map_full', 'Your Map Id', ...
- Create a Mapbox &ccess token (https://www.mapbox.com/help/define-access-token/)
- Add it to map.lens : L.mapbox.accessToken= 'Your Koken Access Token';
- Save the map.lens and upload the file to /storage/theme/your_theme/

## Configuration of the map, from the script by pnizet 
see : https://github.com/pnizet/koken_mapbox
- It will display 250 markers (max loop), you can change the number of markers displayed by changing the line 51
- If you left the code untouched the map will be centred on the median coordinate of all the markers
- If you prefer to display a map that fits all the markers uncomments line of the section "// Fits map to markers..."

## With some additions:
- it uses spiders on the lower zoom level when pictures share the same coordinates (see the section "// Mapbox spiders")
- load the map twice due to a bug mention in the koken forum (see the section "//Check if the current URL contains '#'")
- the height of the map will be reduce if the screen is less thant 766px (for mobile phone)
```css
#map_full { top:0; bottom:0; width:100%; height: 450px; margin-top: -5px;}
@media screen and (min-width: 766px) {
	#map_full {
	display: inline-block;
	height: 1000px;
	width: 100%;
	}
}
```
- makes able to pass coordinates in the URL of your map from content.lens to directly zoom around it (see the section "// Is there coordinates in URL from content.lens ?") 

## Link your pictures in content.lens with your map:
see : http://www.here-and-there-pics.me/albums/ladakh-india/timeline/parvati-valley-in-the-kullu-district-of-himachal-pradesh/

-- Just add the loop inside your template or its child, inside the content.lens (next to the exif in my case) 
```css
<koken:geolocation>
	<koken:not empty="geolocation.latitude">
	<a href="http://www.YourUrlForYourMap.eu/?qlong={{ geolocation.longitude }}&qlat={{ geolocation.latitude }}">
	View on a map</a>
	</koken:not>
</koken:geolocation>
```
- And replace YourUrlForYourMap (e.g. http://www.here-and-there-pics.me/map/?qlong={{ geolocation.longitude }}&qlat={{ geolocation.latitude }})

That it !
