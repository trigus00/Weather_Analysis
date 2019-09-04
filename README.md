# Weather_Analysis

Declaring Dependnecies
# Declare Dependencies 
from bs4 import BeautifulSoup
from splinter import Browser
import pandas as pd
import requests
# https://splinter.readthedocs.io/en/latest/drivers/chrome.html
!which chromedriver
/usr/local/bin/chromedriver
Article Scraping
#ignitiated dummy website to scrape the data: 

executable_path = {'executable_path': '/usr/local/bin/chromedriver'}
browser = Browser('chrome', **executable_path, headless=False)
#url we want to scrape 
url = 'https://mars.nasa.gov/news/?page=0&per_page=40&order=publish_date+desc%2Ccreated_at+desc&search=&category=19%2C165%2C184%2C204&blank_scope=Latest'
browser.visit(url)
# establishing connection with beautiful soup 

html = browser.html
soup = BeautifulSoup(html, 'html.parser')

news_titles = soup.find_all('div', class_='content_title')
news_p = soup.find_all('div', class_='rollover_description_inner')
for title in news_titles:
    print('-----------')
    print(title.text)
-----------
NASA Invites Students to Name Mars 2020 Rover
-----------
NASA's Mars Helicopter Attached to Mars 2020 Rover 
-----------
What's Mars Solar Conjunction, and Why Does It Matter?
-----------
Scientists Explore Outback as Testbed for Mars 
-----------
NASA-JPL Names 'Rolling Stones Rock' on Mars
-----------
Robotic Toolkit Added to NASA's Mars 2020 Rover
-----------
Space Samples Link NASA's Apollo 11 and Mars 2020
-----------
Small Satellite Mission of the Year
-----------
NASA 'Optometrists' Verify Mars 2020 Rover's 20/20 Vision
-----------
New Finds for Mars Rover, Seven Years After Landing
-----------
MEDLI2 Installation on Mars 2020 Aeroshell Begins
-----------
NASA's Mars 2020 Rover Does Biceps Curls 
-----------
Fueling of NASA's Mars 2020 Rover Power System Begins
-----------
What Does a Marsquake Look Like?
-----------
Mars 2020 Rover: T-Minus One Year and Counting 
-----------
NASA Racks Up Two Emmy Nominations for Mission Coverage
-----------
Want to Colonize Mars? Aerogel Could Help
-----------
A Rover Pit Stop at JPL
-----------
Mars 2020 Rover Gets a Super Instrument
-----------
A Neil Armstrong for Mars: Landing the Mars 2020 Rover
-----------
NASA's InSight Uncovers the 'Mole' 
-----------
Mars 2020 Rover's 7-Foot-Long Robotic Arm Installed
-----------
NASA Selects Partners for Mars 2020 'Name the Rover' Contest, Seeks Judges
-----------
Curiosity's Mars Methane Mystery Continues
-----------
Mars 2020 Rover Gets Its Wheels
-----------
The Mast Is Raised for NASA's Mars 2020 Rover
-----------
NASA's Mars 2020 Will Blaze a Trail — for Humans
-----------
Johnson-Built Device to Help Mars 2020 Rover Search for Signs of Life
-----------
Watch NASA Build Its Next Mars Rover
-----------
NASA's Mars Helicopter Testing Enters Final Phase
-----------
InSight's Team Tries New Strategy to Help the 'Mole'
-----------
Common Questions about InSight's 'Mole'
-----------
NASA's Curiosity Mars Rover Finds a Clay Cache
-----------
NASA to Land in Mars, Pennsylvania to Celebrate Red Planet with STEAM
-----------
NASA's Mars 2020 Gets a Dose of Space Here on Earth
-----------
NASA Invites Public to Submit Names to Fly Aboard Next Mars Rover
-----------
NASA's MRO Completes 60,000 Trips Around Mars
-----------
Video: Fly over Mount Sharp on Mars
-----------
Why This Martian Full Moon Looks Like Candy
-----------
For InSight, Dust Cleanings Will Yield New Science
-----------


NASA Garners 7 Webby Award Nominations


-----------


NASA's Opportunity Rover Mission on Mars Comes to End


-----------


NASA's InSight Places First Instrument on Mars


-----------


NASA Invites Students to Name Mars 2020 Rover


-----------


NASA's Curiosity Mars Rover Finds a Clay Cache


-----------


Why This Martian Full Moon Looks Like Candy


-----------


NASA Garners 7 Webby Award Nominations


-----------


NASA's Opportunity Rover Mission on Mars Comes to End


-----------


NASA's InSight Places First Instrument on Mars


-----------


NASA Invites Students to Name Mars 2020 Rover


-----------


NASA's Curiosity Mars Rover Finds a Clay Cache


-----------


Why This Martian Full Moon Looks Like Candy


for description in news_p:
    print('-----------')
    print(description.text )
-----------
Through Nov. 1, K-12 students in the U.S. are encouraged to enter an essay contest to name NASA's next Mars rover.
-----------
The helicopter will be first aircraft to perform flight tests on another planet.
-----------
NASA spacecraft at Mars are going to be on their own for a few weeks when the Sun comes between Mars and Earth, interrupting communications.
-----------
Australia provides a great place for NASA's Mars 2020 and the ESA-Roscosmos ExoMars scientists to hone techniques in preparation for searching for signs ancient life on Mars.
-----------
NASA's Mars InSight mission honored one of the biggest bands of all time at Pasadena concert.
-----------
The bit carousel, which lies at the heart of the rover's Sample Caching System, is now aboard NASA's newest rover. 
-----------
While separated by half a century, NASA's Apollo 11 and Mars 2020 missions share the same historic goal: returning samples to Earth.
-----------
The first interplanetary CubeSats were recognized by the engineering community with the 2019 Small Satellite Mission of the Year award.
-----------
Mars 2020 rover underwent an eye exam after several cameras were installed on the rover.
-----------
NASA's Curiosity rover is discovering odd rocks halfway into a region called the "clay-bearing unit."
-----------
Hardware installed onto NASA's Mars 2020 entry vehicle this week will help to increase the safety of future Mars landings.
-----------
In this time-lapse video, the robotic arm on NASA's Mars 2020 rover maneuvers its 88-pound (40-kilogram) sensor-laden turret as it moves from a deployed to stowed configuration.
-----------
NASA gives the go-ahead to fuel the Mars 2020 rover's Multi-Mission Radioisotope Thermoelectric Generator, which will power rover and help keep it warm while exploring Mars.
-----------
InSight scientists used a special "shake room" to demonstrate the differences between quakes on Earth, the Moon and Mars.
-----------
The launch period for NASA's next rover, Mars 2020, opens exactly one year from today, July 17, 2020, and extends through Aug. 5, 2020.
-----------
JPL's coverage of the Mars InSight mission is among the efforts that will be up for an award in mid-September.
-----------
Researchers are studying whether a wonder material used in Mars rovers could help warm parts of the Red Planet rich in water ice.
-----------
Working like a finely honed machine, a team of engineers in this time-lapse video clip install test wheels on another finely honed machine: NASA's Mars 2020 rover.
-----------
With its rock-zapping laser, the SuperCam will enable the science team to identify the chemical and mineral makeup of its targets on the Red Planet.
-----------
NASA's newest rover will have an autopilot called Terrain-Relative Navigation.
-----------
The lander's robotic arm has successfully removed a piece of hardware blocking the view of its digging device in order to help with recovery efforts.
-----------
The main robotic arm has been installed on NASA's newest rover. When complete, the arm will enable the rover to hold and use science tools like a human geologist would.
-----------
The contest for U.S. schoolchildren will open in fall 2019, but judges can sign up now.
-----------
The Curiosity rover’s follow-on sampling shows last week’s methane levels have sharply decreased.
-----------
With the mobility suspension in place, the rover not only looks more like a rover but has many of its 'big-ticket items' installed.
-----------
Engineers at JPL take a group selfie after attaching the remote sensing mast to the Mars 2020 rover.
-----------
The next robotic Mars mission will carry technology that will help enable astronauts to eventually explore the Red Planet.
-----------
NASA’s Johnson Space Center (JSC) recently built a new calibration device for the rover to check SHERLOC’s function and properly tune it during the upcoming mission.
-----------
A newly installed webcam offers the public a live, bird's-eye view of NASA's Mars 2020 rover as it takes shape at NASA's Jet Propulsion Laboratory. 
-----------
NASA's Mars Helicopter flight demonstration project has passed a number of key tests with flying colors.
-----------
The spacecraft's robotic arm will lift the heat probe's support structure, providing a better look at the instrument that has been trying to burrow into the Martian surface.
-----------
There's a new plan to get InSight's "mole" moving again. The following Q&As with two members of the team answer some of the most common questions about the burrowing device, part of a science instrument called the Heat Flow and Physical Properties Package (HP3).
-----------
The rover recently drilled two samples, and both showed the highest levels of clay ever found during the mission.
-----------
NASA returns to Mars, Pennsylvania Friday, May 31 to celebrate Mars exploration and share the agency’s excitement about landing astronauts on the Moon in five years.
-----------
NASA's Mars 2020 spacecraft has completed tests that are the best Earthly approximations of what the spacecraft will endure during launch and interplanetary cruise.
-----------
From now till Sept. 30, the public can submit names to be stenciled on chips that will fly on the Mars 2020 rover and receive a souvenir boarding pass.
-----------
The orbiting spacecraft is also about to set a record for data relayed from the Martian surface.
-----------
A new animation shows the region NASA's Curiosity rover is currently exploring and where its team wants to go in the future.
-----------
For the first time, NASA's Mars Odyssey orbiter has caught the Martian moon Phobos during a full moon phase. Each color in this new image represents a temperature range detected by Odyssey's infrared camera.
-----------
Wind can be crucial to clearing dust from spacecraft solar panels on Mars. With InSight's meteorological sensors, scientists get their first measurements of wind and dust interacting "live" on the Martian surface.  
-----------

Nominees include four JPL projects: the solar system and climate websites, InSight social media, and a 360-degree Earth video. Public voting closes April 18, 2019.

-----------

NASA's Opportunity Mars rover mission is complete after 15 years on Mars. Opportunity's record-breaking exploration laid the groundwork for future missions to the Red Planet.

-----------

In deploying its first instrument onto the surface of Mars, the lander completes a major mission milestone.

-----------

Through Nov. 1, K-12 students in the U.S. are encouraged to enter an essay contest to name NASA's next Mars rover.

-----------

The rover recently drilled two samples, and both showed the highest levels of clay ever found during the mission.

-----------

For the first time, NASA's Mars Odyssey orbiter has caught the Martian moon Phobos during a full moon phase. Each color in this new image represents a temperature range detected by Odyssey's infrared camera.

-----------

Nominees include four JPL projects: the solar system and climate websites, InSight social media, and a 360-degree Earth video. Public voting closes April 18, 2019.

-----------

NASA's Opportunity Mars rover mission is complete after 15 years on Mars. Opportunity's record-breaking exploration laid the groundwork for future missions to the Red Planet.

-----------

In deploying its first instrument onto the surface of Mars, the lander completes a major mission milestone.

-----------

Through Nov. 1, K-12 students in the U.S. are encouraged to enter an essay contest to name NASA's next Mars rover.

-----------

The rover recently drilled two samples, and both showed the highest levels of clay ever found during the mission.

-----------

For the first time, NASA's Mars Odyssey orbiter has caught the Martian moon Phobos during a full moon phase. Each color in this new image represents a temperature range detected by Odyssey's infrared camera.

Image scraping
#image scraping 
featured_image_url = 'https://www.jpl.nasa.gov/spaceimages/?search=&category=Mars'
browser.visit(featured_image_url)
html = browser.html
soup = BeautifulSoup(html, 'html.parser')
#scraping the image 
featured_image = soup.find('article')['style'].replace('background-image: url(','').replace(');', '')
featured_image = featured_image[1:-1]
#url main website and image website 
main_url = 'https://www.jpl.nasa.gov'
image_url= main_url + featured_image
# link to the website 
print (image_url)
https://www.jpl.nasa.gov/spaceimages/images/wallpaper/PIA17254-1920x1200.jpg
Twitter Scraping
#twitter scraping 
mars_weather_twitter = 'https://twitter.com/marswxreport?lang=en' 
browser.visit(mars_weather_twitter)
html = browser.html
soup = BeautifulSoup(html, 'html.parser')
#finding latest tweets on Mars Twitter acount 
latest_tweet = soup.find_all('div', class_='js-tweet-text-container')
for tweet in latest_tweet:
    weather_tweets = tweet.find('p').text
    if 'sol' and 'pressure' in weather_tweets:
        print (weather_tweets)
        print("------------------------------------------------------------------------------------------------------");
    else: 
        pass
InSight sol 265 (2019-08-25) low -99.4ºC (-146.9ºF) high -26.3ºC (-15.3ºF)
winds from the SSE at 5.3 m/s (12.0 mph) gusting to 16.1 m/s (35.9 mph)
pressure at 7.50 hPapic.twitter.com/9YLawm67zS
------------------------------------------------------------------------------------------------------
InSight sol 264 (2019-08-24) low -101.0ºC (-149.7ºF) high -26.7ºC (-16.1ºF)
winds from the SW at 4.4 m/s (9.9 mph) gusting to 17.4 m/s (38.9 mph)
pressure at 7.60 hPapic.twitter.com/xIytu1MnDG
------------------------------------------------------------------------------------------------------
InSight sol 263 (2019-08-23) low -100.9ºC (-149.6ºF) high -27.2ºC (-17.0ºF)
winds from the SW at 4.1 m/s (9.2 mph) gusting to 18.3 m/s (40.9 mph)
pressure at 7.60 hPa
------------------------------------------------------------------------------------------------------
InSight sol 262 (2019-08-22) low -101.3ºC (-150.3ºF) high -26.4ºC (-15.6ºF)
winds from the SSE at 4.2 m/s (9.4 mph) gusting to 15.8 m/s (35.3 mph)
pressure at 7.60 hPa
------------------------------------------------------------------------------------------------------
InSight sol 261 (2019-08-21) low -102.4ºC (-152.4ºF) high -26.6ºC (-15.8ºF)
winds from the SSE at 4.9 m/s (11.0 mph) gusting to 16.0 m/s (35.8 mph)
pressure at 7.70 hPapic.twitter.com/MhPPOHJg3m
------------------------------------------------------------------------------------------------------
InSight sol 260 (2019-08-20) low -101.7ºC (-151.1ºF) high -28.6ºC (-19.5ºF)
pressure at 7.60 hPa
------------------------------------------------------------------------------------------------------
InSight sol 259 (2019-08-19) low -101.0ºC (-149.8ºF) high -27.1ºC (-16.9ºF)
winds from the SW at 4.3 m/s (9.6 mph) gusting to 17.6 m/s (39.4 mph)
pressure at 7.60 hPa
------------------------------------------------------------------------------------------------------
InSight sol 258 (2019-08-18) low -100.0ºC (-148.1ºF) high -26.2ºC (-15.2ºF)
winds from the SSE at 5.3 m/s (11.9 mph) gusting to 16.8 m/s (37.6 mph)
pressure at 7.60 hPapic.twitter.com/5nCVjcsmlZ
------------------------------------------------------------------------------------------------------
InSight sol 257 (2019-08-17) low -100.2ºC (-148.4ºF) high -26.5ºC (-15.7ºF)
winds from the SSE at 4.4 m/s (9.8 mph) gusting to 17.1 m/s (38.2 mph)
pressure at 7.60 hPapic.twitter.com/hBQzJWARH0
------------------------------------------------------------------------------------------------------
InSight sol 256 (2019-08-16) low -101.7ºC (-151.1ºF) high -25.6ºC (-14.2ºF)
winds from the SW at 4.2 m/s (9.4 mph) gusting to 17.9 m/s (40.0 mph)
pressure at 7.60 hPa
------------------------------------------------------------------------------------------------------
InSight sol 255 (2019-08-15) low -100.1ºC (-148.1ºF) high -24.7ºC (-12.4ºF)
winds from the SSW at 4.5 m/s (10.0 mph) gusting to 17.3 m/s (38.6 mph)
pressure at 7.60 hPa
------------------------------------------------------------------------------------------------------
InSight sol 254 (2019-08-14) low -99.3ºC (-146.7ºF) high -25.9ºC (-14.6ºF)
winds from the SE at 4.9 m/s (10.9 mph) gusting to 18.1 m/s (40.5 mph)
pressure at 7.60 hPa
------------------------------------------------------------------------------------------------------
InSight sol 253 (2019-08-13) low -100.0ºC (-148.1ºF) high -25.5ºC (-13.9ºF)
winds from the SSE at 4.6 m/s (10.3 mph) gusting to 16.4 m/s (36.6 mph)
pressure at 7.60 hPapic.twitter.com/OnwaHAaYRH
------------------------------------------------------------------------------------------------------
InSight sol 252 (2019-08-12) low -100.8ºC (-149.4ºF) high -26.0ºC (-14.8ºF)
winds from the SSW at 4.4 m/s (9.8 mph) gusting to 18.3 m/s (40.9 mph)
pressure at 7.60 hPapic.twitter.com/WY3JQBXVuU
------------------------------------------------------------------------------------------------------
InSight sol 251 (2019-08-11) low -101.0ºC (-149.7ºF) high -26.5ºC (-15.8ºF)
winds from the SSE at 4.1 m/s (9.2 mph) gusting to 17.5 m/s (39.1 mph)
pressure at 7.60 hPapic.twitter.com/9mgFzHl8t3
------------------------------------------------------------------------------------------------------
InSight sol 250 (2019-08-10) low -100.0ºC (-148.1ºF) high -26.2ºC (-15.1ºF)
winds from the SSE at 4.4 m/s (9.8 mph) gusting to 16.2 m/s (36.2 mph)
pressure at 7.60 hPapic.twitter.com/9sZRRUi3dm
------------------------------------------------------------------------------------------------------
InSight sol 249 (2019-08-09) low -98.8ºC (-145.8ºF) high -26.0ºC (-14.8ºF)
winds from the SSE at 4.4 m/s (9.8 mph) gusting to 17.5 m/s (39.1 mph)
pressure at 7.60 hPapic.twitter.com/jDOsvHTwYg
------------------------------------------------------------------------------------------------------
Mars Facts
#image scraping 
mars_facts = 'https://space-facts.com/mars/'
browser.visit(mars_facts)
html = browser.html
soup = BeautifulSoup(html,'html.parser')
facts = soup.find_all('table', class_='tablepress tablepress-id-p-mars')
my_table = soup.find('table',{'class':'tablepress tablepress-id-p-mars'})
my_table
<table class="tablepress tablepress-id-p-mars" id="tablepress-p-mars"><tbody><tr class="row-1 odd"><td class="column-1"><strong>Equatorial Diameter:</strong></td><td class="column-2">6,792 km<br/></td></tr><tr class="row-2 even"><td class="column-1"><strong>Polar Diameter:</strong></td><td class="column-2">6,752 km<br/></td></tr><tr class="row-3 odd"><td class="column-1"><strong>Mass:</strong></td><td class="column-2">6.39 × 10^23 kg<br/> (0.11 Earths)</td></tr><tr class="row-4 even"><td class="column-1"><strong>Moons:</strong></td><td class="column-2">2 (<a href="https://space-facts.com/moons/phobos/">Phobos</a> &amp; <a href="https://space-facts.com/moons/deimos/">Deimos</a>)</td></tr><tr class="row-5 odd"><td class="column-1"><strong>Orbit Distance:</strong></td><td class="column-2">227,943,824 km<br/> (1.38 AU)</td></tr><tr class="row-6 even"><td class="column-1"><strong>Orbit Period:</strong></td><td class="column-2">687 days (1.9 years)<br/></td></tr><tr class="row-7 odd"><td class="column-1"><strong>Surface Temperature: </strong></td><td class="column-2">-87 to -5 °C</td></tr><tr class="row-8 even"><td class="column-1"><strong>First Record:</strong></td><td class="column-2">2nd millennium BC</td></tr><tr class="row-9 odd"><td class="column-1"><strong>Recorded By:</strong></td><td class="column-2">Egyptian astronomers</td></tr></tbody></table>
info = my_table.find_all('tr')
mars_facts = [] 
for i in info:
    row = i 
    mars_facts.append(row.get_text('').split(':'))
    
row = 0
columns = []
while row < 9:
    columns.append(mars_facts[row][0])
    row = row + 1 
columns
['Equatorial Diameter',
 'Polar Diameter',
 'Mass',
 'Moons',
 'Orbit Distance',
 'Orbit Period',
 'Surface Temperature',
 'First Record',
 'Recorded By']
columns
['Equatorial Diameter',
 'Polar Diameter',
 'Mass',
 'Moons',
 'Orbit Distance',
 'Orbit Period',
 'Surface Temperature',
 'First Record',
 'Recorded By']
row = 0
columns_1 = []

while row < 9:
    columns_1.append(mars_facts[row][1])
    row = row + 1 
columns_1
['6,792 km',
 '6,752 km',
 '6.39 × 10^23 kg (0.11 Earths)',
 '2 (Phobos & Deimos)',
 '227,943,824 km (1.38 AU)',
 '687 days (1.9 years)',
 ' -87 to -5 °C',
 '2nd millennium BC',
 'Egyptian astronomers']
mars_df =pd.DataFrame()
mars_df['Description'] = columns
mars_df['Values']=columns_1
mars_df
Description	Values
0	Equatorial Diameter	6,792 km
1	Polar Diameter	6,752 km
2	Mass	6.39 × 10^23 kg (0.11 Earths)
3	Moons	2 (Phobos & Deimos)
4	Orbit Distance	227,943,824 km (1.38 AU)
5	Orbit Period	687 days (1.9 years)
6	Surface Temperature	-87 to -5 °C
7	First Record	2nd millennium BC
8	Recorded By	Egyptian astronomers
Mars Hemisphere
#image scraping 
mars_hemispheres = 'https://astrogeology.usgs.gov/search/results?q=hemisphere+enhanced&k1=target&v1=Mars'
browser.visit(mars_hemispheres)
html = browser.html
soup = BeautifulSoup(html, 'html.parser')
#hempisphere URLS 
hemisphere_image_urls = []
main_url = 'https://astrogeology.usgs.gov'

image_items = soup.find_all('div',class_='item')

print(image_items)
[<div class="item"><a class="itemLink product-item" href="/search/map/Mars/Viking/cerberus_enhanced"><img alt="Cerberus Hemisphere Enhanced thumbnail" class="thumb" src="/cache/images/dfaf3849e74bf973b59eb50dab52b583_cerberus_enhanced.tif_thumb.png"/></a><div class="description"><a class="itemLink product-item" href="/search/map/Mars/Viking/cerberus_enhanced"><h3>Cerberus Hemisphere Enhanced</h3></a><span class="subtitle" style="float:left">image/tiff 21 MB</span><span class="pubDate" style="float:right"></span><br/><p>Mosaic of the Cerberus hemisphere of Mars projected into point perspective, a view similar to that which one would see from a spacecraft. This mosaic is composed of 104 Viking Orbiter images acquired…</p></div> <!-- end description --></div>, <div class="item"><a class="itemLink product-item" href="/search/map/Mars/Viking/schiaparelli_enhanced"><img alt="Schiaparelli Hemisphere Enhanced thumbnail" class="thumb" src="/cache/images/7677c0a006b83871b5a2f66985ab5857_schiaparelli_enhanced.tif_thumb.png"/></a><div class="description"><a class="itemLink product-item" href="/search/map/Mars/Viking/schiaparelli_enhanced"><h3>Schiaparelli Hemisphere Enhanced</h3></a><span class="subtitle" style="float:left">image/tiff 35 MB</span><span class="pubDate" style="float:right"></span><br/><p>Mosaic of the Schiaparelli hemisphere of Mars projected into point perspective, a view similar to that which one would see from a spacecraft. The images were acquired in 1980 during early northern…</p></div> <!-- end description --></div>, <div class="item"><a class="itemLink product-item" href="/search/map/Mars/Viking/syrtis_major_enhanced"><img alt="Syrtis Major Hemisphere Enhanced thumbnail" class="thumb" src="/cache/images/aae41197e40d6d4f3ea557f8cfe51d15_syrtis_major_enhanced.tif_thumb.png"/></a><div class="description"><a class="itemLink product-item" href="/search/map/Mars/Viking/syrtis_major_enhanced"><h3>Syrtis Major Hemisphere Enhanced</h3></a><span class="subtitle" style="float:left">image/tiff 25 MB</span><span class="pubDate" style="float:right"></span><br/><p>Mosaic of the Syrtis Major hemisphere of Mars projected into point perspective, a view similar to that which one would see from a spacecraft. This mosaic is composed of about 100 red and violet…</p></div> <!-- end description --></div>, <div class="item"><a class="itemLink product-item" href="/search/map/Mars/Viking/valles_marineris_enhanced"><img alt="Valles Marineris Hemisphere Enhanced thumbnail" class="thumb" src="/cache/images/04085d99ec3713883a9a57f42be9c725_valles_marineris_enhanced.tif_thumb.png"/></a><div class="description"><a class="itemLink product-item" href="/search/map/Mars/Viking/valles_marineris_enhanced"><h3>Valles Marineris Hemisphere Enhanced</h3></a><span class="subtitle" style="float:left">image/tiff 27 MB</span><span class="pubDate" style="float:right"></span><br/><p>Mosaic of the Valles Marineris hemisphere of Mars projected into point perspective, a view similar to that which one would see from a spacecraft. The distance is 2500 kilometers from the surface of…</p></div> <!-- end description --></div>]
for link in image_items:
    image_name = link.find('h3').get_text
    image_find = link.find('a', class_='itemLink product-item')['href']
    link_to_image = main_url + image_find 
    
    #opening another website using link to image 
    
    browser.visit(link_to_image)
    image_html = browser.html
    soup = BeautifulSoup(image_html, 'html.parser')
    image_url = main_url + soup.find('img', class_='wide-image')['src']
    
    print(image_url)
    
    hemisphere_image_urls.append({"title": image_name , "image_url": image_url})

    
    
https://astrogeology.usgs.gov/cache/images/cfa62af2557222a02478f1fcd781d445_cerberus_enhanced.tif_full.jpg
https://astrogeology.usgs.gov/cache/images/3cdd1cbf5e0813bba925c9030d13b62e_schiaparelli_enhanced.tif_full.jpg
https://astrogeology.usgs.gov/cache/images/ae209b4e408bb6c3e67b6af38168cf28_syrtis_major_enhanced.tif_full.jpg
https://astrogeology.usgs.gov/cache/images/7cf2da4bf549ed01c17f206327be4db7_valles_marineris_enhanced.tif_full.jpg
hemisphere_image_urls
[{'title': <bound method Tag.get_text of <h3>Cerberus Hemisphere Enhanced</h3>>,
  'image_url': 'https://astrogeology.usgs.gov/cache/images/cfa62af2557222a02478f1fcd781d445_cerberus_enhanced.tif_full.jpg'},
 {'title': <bound method Tag.get_text of <h3>Schiaparelli Hemisphere Enhanced</h3>>,
  'image_url': 'https://astrogeology.usgs.gov/cache/images/3cdd1cbf5e0813bba925c9030d13b62e_schiaparelli_enhanced.tif_full.jpg'},
 {'title': <bound method Tag.get_text of <h3>Syrtis Major Hemisphere Enhanced</h3>>,
  'image_url': 'https://astrogeology.usgs.gov/cache/images/ae209b4e408bb6c3e67b6af38168cf28_syrtis_major_enhanced.tif_full.jpg'},
 {'title': <bound method Tag.get_text of <h3>Valles Marineris Hemisphere Enhanced</h3>>,
  'image_url': 'https://astrogeology.usgs.gov/cache/images/7cf2da4bf549ed01c17f206327be4db7_valles_marineris_enhanced.tif_full.jpg'}]
 

