WeatherPy
Note
Instructions have been included for each segment. You do not have to follow them exactly, but they are included to help you think through the steps.
# Dependencies and Setup
import matplotlib.pyplot as plt
import pandas as pd
import numpy as np
import requests
import time
import pprint
import csv


# Import API key
from api_keys import api_key

# Incorporated citipy to determine city based on latitude and longitude
from citipy import citipy

# Output File (CSV)
output_data_file = "output_data/cities.csv"

# Range of latitudes and longitudes
lat_range = (-90, 90)
lng_range = (-180, 180)
Generate Cities List
# List for holding lat_lngs and cities
lat_lngs = []
cities = []

# Create a set of random lat and lng combinations
lats = np.random.uniform(low=-90.000, high=90.000, size=1500)
lngs = np.random.uniform(low=-180.000, high=180.000, size=1500)
lat_lngs = zip(lats, lngs)

# Identify nearest city for each lat, lng combination
for lat_lng in lat_lngs:
    city = citipy.nearest_city(lat_lng[0], lat_lng[1]).city_name
    # Replace spaces with %20 to create url correctly 
    city = city.replace(" ", "%20")
    
    # If the city is unique, then add it to a our cities list
    if city not in cities:
        cities.append(city)

# Print the city count to confirm sufficient count
len(cities)
pp = pprint.PrettyPrinter(indent=4)
pp.pprint(cities)
[   'yichun',
    'busselton',
    'karaul',
    'khatanga',
    'hermanus',
    'kilmez',
    'ushuaia',
    'punta%20arenas',
    'mataura',
    'belushya%20guba',
    'montepuez',
    'souillac',
    'arraial%20do%20cabo',
    'tiksi',
    'ryotsu',
    'uvira',
    'mpika',
    'menongue',
    'muroto',
    'sabha',
    'taltal',
    'daru',
    'ploemeur',
    'port%20elizabeth',
    'albany',
    'hihifo',
    'cidreira',
    'nikolskoye',
    'hobart',
    'huilong',
    'san%20policarpo',
    'vestmannaeyjar',
    'barentsburg',
    'lompoc',
    'hithadhoo',
    'los%20llanos%20de%20aridane',
    'qaanaaq',
    'buarcos',
    'najran',
    'dunedin',
    'talara',
    'puerto%20ayora',
    'pisco',
    'mayo',
    'richards%20bay',
    'kaolinovo',
    'bac%20lieu',
    'esperance',
    'invermere',
    'rikitea',
    'port%20hedland',
    'saldanha',
    'new%20norfolk',
    'doka',
    'cape%20town',
    'kazalinsk',
    'iwanai',
    'bluff',
    'yellowknife',
    'horadiz',
    'san%20patricio',
    'saint%20george',
    'saint-philippe',
    'codrington',
    'tautira',
    'valdivia',
    'jumla',
    'hambantota',
    'dali',
    'sao%20joao%20da%20barra',
    'ternate',
    'belyy%20yar',
    'umzimvubu',
    'vaini',
    'berdigestyakh',
    'samusu',
    'darhan',
    'mys%20shmidta',
    'tumannyy',
    'ribeira%20grande',
    'kommunar',
    'tilichiki',
    'kindu',
    'tasiilaq',
    'barrow',
    'comodoro%20rivadavia',
    'isangel',
    'honningsvag',
    'jamestown',
    'qaqortoq',
    'adrar',
    'hilo',
    'dwarka',
    'yulin',
    'dudinka',
    'coquimbo',
    'broome',
    'atuona',
    'avarua',
    'marfino',
    'cabo%20san%20lucas',
    'bairiki',
    'voh',
    'ahipara',
    'kachug',
    'alekseyevskaya',
    'amderma',
    'tuktoyaktuk',
    'east%20london',
    'tsihombe',
    'lagoa',
    'xining',
    'ippy',
    'pevek',
    'bengkulu',
    'ust-kuyga',
    'arrifes',
    'poyarkovo',
    'haines%20junction',
    'bukachacha',
    'felanitx',
    'grand%20river%20south%20east',
    'carnarvon',
    'verkhoyansk',
    'kodiak',
    'umm%20lajj',
    'freistadt',
    'illoqqortoormiut',
    'bubaque',
    'lishui',
    'baruun-urt',
    'thompson',
    'mahebourg',
    'kharan',
    'port%20alfred',
    'merauke',
    'nome',
    'mandurah',
    'muzhi',
    'kapaa',
    'shingu',
    'tignere',
    'cherskiy',
    'fortuna',
    'giyani',
    'taolanaro',
    'yuzhno-kurilsk',
    'orange',
    'muros',
    'kendal',
    'kieta',
    'kropotkin',
    'makakilo%20city',
    'mitsamiouli',
    'burnie',
    'antalaha',
    'usinsk',
    'longyearbyen',
    'grand%20gaube',
    'talwara',
    'henties%20bay',
    'faanui',
    'georgetown',
    'sedelnikovo',
    'saleaula',
    'marilandia',
    'mount%20gambier',
    'seia',
    'san%20carlos%20de%20bariloche',
    'northam',
    'avera',
    'phan%20rang',
    'karratha',
    'lerwick',
    'meyungs',
    'atambua',
    'severo-kurilsk',
    'dikson',
    'alta%20floresta',
    'cukai',
    'medford',
    'nykobing',
    'geraldton',
    'ukiah',
    'naze',
    'talnakh',
    'tabas',
    'saint-pierre',
    'sur',
    'ixtapa',
    'saint%20cloud',
    'karlovac',
    'urusha',
    'tura',
    'yibin',
    'leningradskiy',
    'flinders',
    'castro',
    'inuvik',
    'bowmore',
    'yar-sale',
    'nguiu',
    'gorom-gorom',
    'biak',
    'anadyr',
    'hermiston',
    'cap%20malheureux',
    'barra%20velha',
    'zhigansk',
    'hamilton',
    'maracaibo',
    'marsh%20harbour',
    'manokwari',
    'homer',
    'vila%20velha',
    'hami',
    'acapulco',
    'hasaki',
    'chuy',
    'iqaluit',
    'yuanping',
    'poum',
    'yumen',
    'ende',
    'cockburn%20town',
    'louisbourg',
    'mar%20del%20plata',
    'narsaq',
    'eftimie%20murgu',
    'xichang',
    'lesogorsk',
    'butaritari',
    'marystown',
    'indianola',
    'mandera',
    'nanortalik',
    'kismayo',
    'lavrentiya',
    'taitung',
    'satka',
    'attawapiskat',
    'quatre%20cocos',
    'provideniya',
    'constitucion',
    'victoria',
    'bambous%20virieux',
    'port%20macquarie',
    'sao%20filipe',
    'ust-kut',
    'guerrero%20negro',
    'gainesville',
    'bredasdorp',
    'orange%20cove',
    'ilulissat',
    'lesnoy',
    'sitka',
    'elat',
    'san%20quintin',
    'marcona',
    'alofi',
    'xixiang',
    'uray',
    'airai',
    'cheuskiny',
    'iberia',
    'san%20cristobal',
    'warrnambool',
    'alice%20springs',
    'mega',
    'sola',
    'dingle',
    'bud',
    'pompeia',
    'miraflores',
    'rumonge',
    'salvador',
    'ullapool',
    'antofagasta',
    'pemba',
    'ponta%20do%20sol',
    'synya',
    'norman%20wells',
    'port%20hardy',
    'cayenne',
    'kavieng',
    'sistranda',
    'potenza',
    'dubbo',
    'prince%20rupert',
    'na%20wa',
    'auki',
    'broken%20hill',
    'pangnirtung',
    'pochutla',
    'harper',
    'moerai',
    'naranjal',
    'kilindoni',
    'vilhena',
    'chokurdakh',
    'mecca',
    'peshkovo',
    'saskylakh',
    'waddan',
    'sorland',
    'ancud',
    'port%20lincoln',
    'colonia',
    'aykhal',
    'gull%20lake',
    'aksarka',
    'egvekinot',
    'college',
    'bethel',
    'lusaka',
    'ngunguru',
    'luganville',
    'viligili',
    'eucaliptus',
    'nizhneyansk',
    'nioro',
    'huarmey',
    'bathsheba',
    'mentok',
    'korem',
    'timmins',
    'selma',
    'murakami',
    'maragogi',
    'beringovskiy',
    'vaitupu',
    'saint-joseph',
    'bara',
    'erzin',
    'zaraysk',
    'sao%20jose%20da%20coroa%20grande',
    'rocha',
    'batagay-alyta',
    'yulara',
    'mareeba',
    'chiredzi',
    'karla',
    'labuhan',
    'quelimane',
    'krasnyy%20yar',
    'yunjinghong',
    'chambishi',
    'pitimbu',
    'erenhot',
    'morondava',
    'naryan-mar',
    'hay%20river',
    'ucluelet',
    'bandarbeyla',
    'ponta%20delgada',
    'hit',
    'aktash',
    'freeport',
    'strezhevoy',
    'waitati',
    'aklavik',
    'izmalkovo',
    'lata',
    'opuwo',
    'sinnamary',
    'lebu',
    'saint-georges',
    'kankan',
    'bowen',
    'praia%20da%20vitoria',
    'fevralsk',
    'ballina',
    'manama',
    'ewa%20beach',
    'laguna',
    'piacabucu',
    'upernavik',
    'faya',
    'vila%20franca%20do%20campo',
    'pokaran',
    'vao',
    'phrai%20bung',
    'kahului',
    'jacareacanga',
    'zeya',
    'biloela',
    'simao',
    'medea',
    'kupang',
    'candolim',
    'marawi',
    'rawson',
    'nisia%20floresta',
    'galle',
    'itabira',
    'husavik',
    'guatire',
    'rajpur',
    'gao',
    'ulladulla',
    'willmar',
    'tuatapere',
    'eldorado',
    'brownsville',
    'waingapu',
    'arusha',
    'fare',
    'maputo',
    'dakar',
    'sentyabrskiy',
    'shimoda',
    'ambalavao',
    'jizan',
    'sergeyevka',
    'gizo',
    'luderitz',
    'kuche',
    'tinskoy',
    'bereda',
    'coahuayana',
    'vallam',
    'novouzensk',
    'yining',
    'guymon',
    'mabaruma',
    'lasa',
    'samarai',
    'baracoa',
    'buchanan',
    'axim',
    'ylivieska',
    'deputatskiy',
    'azimur',
    'tabou',
    'carbondale',
    'aracoiaba%20da%20serra',
    'banjar',
    'porto%20velho',
    'mirabad',
    'san%20jose',
    'hagenow',
    'vardo',
    'kamenskoye',
    'zhangye',
    'padang',
    'doda',
    'cabedelo',
    'clyde%20river',
    'balakirevo',
    'berbera',
    'lardos',
    'namatanai',
    'warrington',
    'suntar',
    'kaitangata',
    'nizhniy%20odes',
    'buenos%20aires',
    'aktau',
    'katsuura',
    'watari',
    'laela',
    'diapaga',
    'leh',
    'xiongshi',
    'oltu',
    'roald',
    'mrirt',
    'te%20anau',
    'novaya%20lyalya',
    'hirtshals',
    'farap',
    'warri',
    'palabuhanratu',
    'fukue',
    'vinh',
    'kamenka',
    'okaihau',
    'ust-maya',
    'iquitos',
    'paragominas',
    'fonte%20boa',
    'yenagoa',
    'klaksvik',
    'khonuu',
    'kruisfontein',
    'sijunjung',
    'tessalit',
    'dunkwa',
    'kidal',
    'alpena',
    'mizan%20teferi',
    'ola',
    'matamoros',
    'tateyama',
    'petropavlovsk-kamchatskiy',
    'kiruna',
    'dinsor',
    'dmitriyevka',
    'wanaka',
    'borama',
    'plettenberg%20bay',
    'angren',
    'thabazimbi',
    'jieshi',
    'svetlogorsk',
    'pringsewu',
    'kankaanpaa',
    'zarechnyy',
    'ormara',
    'puerto%20el%20triunfo',
    'hamada',
    'atbasar',
    'maposeni',
    'gat',
    'eyemouth',
    'ca%20mau',
    'satitoa',
    'badiraguato',
    'karaton',
    'sibolga',
    'vizinga',
    'bonthe',
    'seybaplaya',
    'muisne',
    'mahibadhoo',
    'portland',
    'hengyang',
    'ifanadiana',
    'kalmunai',
    'nichinan',
    'orlik',
    'mehamn',
    'praia',
    'paamiut',
    'tayu',
    'santa%20marinella',
    'sorkjosen',
    'aljezur',
    'kautokeino',
    'oktyabrskiy',
    'licata',
    'maimon',
    'nyurba',
    'harrisonville',
    'mocuba',
    'price',
    'melfort',
    'ostrovnoy',
    'nova%20olinda%20do%20norte',
    'astoria',
    'copiapo',
    'talcahuano',
    'valsad',
    'phalodi',
    'byron%20bay',
    'colac',
    'mount%20pleasant',
    'kralendijk',
    'beyneu',
    'ambulu',
    'vung%20tau',
    'coos%20bay',
    'tabialan',
    'letterkenny',
    'kavaratti',
    'fort%20nelson',
    'calvinia',
    'goldsboro',
    'caravelas',
    'sabzevar',
    'araouane',
    'karamay',
    'clermont',
    'valparaiso',
    'namibe',
    'urumqi',
    'gornopravdinsk',
    'berlevag',
    'douglas',
    'hanzhong',
    'keuruu',
    'andenes',
    'awjilah',
    'necochea',
    'sobolevo',
    'hawera',
    'srednekolymsk',
    'ketchikan',
    'rio%20verde%20de%20mato%20grosso',
    'verkhoturye',
    'basoko',
    'metkovic',
    'mount%20isa',
    'turukhansk',
    'koslan',
    'tual',
    'ndiekro',
    'oranjestad',
    'charlottesville',
    'moindou',
    'ikon-khalk',
    'yeehaw%20junction',
    'wismar',
    'komsomolskiy',
    'goderich',
    'santa%20cecilia',
    'chermoz',
    'segovia',
    'makushino',
    'derzhavinsk',
    'mogadishu']

#Perform API Calls
#Perform a weather check on each city using a series of successive API calls.
#Include a print log of each city as it'sbeing processed (with the city number and city name).

#creating an empty list 

city_name = []
cloudiness = []
country = []
date = []
humidity = []
lat = []
lng = []
max_temp = []
wind_speed = []





#api to retrieve the city
url = "http://api.openweathermap.org/data/2.5/weather?"

record = 1 
count = 1 
sets = 50

print ("---Beginning Data Retrieval---")

for city in cities: 

    query_url = url + "appid=" + api_key + "&q="+city
    
    try:
        city_data = requests.get(query_url).json()
        
        city_name.append(city_data["name"])
        
        cloudiness.append(city_data["clouds"]["all"])            
        
        country.append(city_data["sys"]["country"])
            
        date.append(city_data["dt"])
        
        humidity.append(city_data["main"]["humidity"])
        
        max_temp.append(city_data["main"]["temp_max"])
            
        lat.append(city_data["coord"]["lat"])
        
        lng.append(city_data["coord"]["lon"])
        
        wind_speed.append(city_data["wind"]["speed"])
        
        city_record = city_data["name"]
        
        print(f"Processing Record {record}| {city_record}")
        print(f"{query_url}") 
        record = record +1 
        
        # Wait a second in loop to not over exceed rate limit of API
        time.sleep(1)
    
   

    except:
        print ("city not found ... skipping ")
    continue 

    
       
print ("---Data Retrieval Complete ---")       
          
       
        
        
        
    
      
        
---Beginning Data Retrieval---
Processing Record 1| Yichun
http://api.openweathermap.org/data/2.5/weather?appid=cd80ea31f0dcfaa9dffb1cd446d9a99b&q=yichun
Processing Record 2| Busselton
http://api.openweathermap.org/data/2.5/weather?appid=cd80ea31f0dcfaa9dffb1cd446d9a99b&q=busselton
city not found ... skipping 
Processing Record 3| Khatanga
http://api.openweathermap.org/data/2.5/weather?appid=cd80ea31f0dcfaa9dffb1cd446d9a99b&q=khatanga
Processing Record 4| Hermanus
http://api.openweathermap.org/data/2.5/weather?appid=cd80ea31f0dcfaa9dffb1cd446d9a99b&q=hermanus
city not found ... skipping 
Processing Record 5| Ushuaia
http://api.openweathermap.org/data/2.5/weather?appid=cd80ea31f0dcfaa9dffb1cd446d9a99b&q=ushuaia
Processing Record 6| Punta Arenas
http://api.openweathermap.org/data/2.5/weather?appid=cd80ea31f0dcfaa9dffb1cd446d9a99b&q=punta%20arenas
Processing Record 7| Mataura
http://api.openweathermap.org/data/2.5/weather?appid=cd80ea31f0dcfaa9dffb1cd446d9a99b&q=mataura
city not found ... skipping 
Processing Record 8| Montepuez
http://api.openweathermap.org/data/2.5/weather?appid=cd80ea31f0dcfaa9dffb1cd446d9a99b&q=montepuez
Processing Record 9| Souillac
http://api.openweathermap.org/data/2.5/weather?appid=cd80ea31f0dcfaa9dffb1cd446d9a99b&q=souillac
Processing Record 10| Arraial do Cabo
http://api.openweathermap.org/data/2.5/weather?appid=cd80ea31f0dcfaa9dffb1cd446d9a99b&q=arraial%20do%20cabo
Processing Record 11| Tiksi
http://api.openweathermap.org/data/2.5/weather?appid=cd80ea31f0dcfaa9dffb1cd446d9a99b&q=tiksi
Processing Record 12| Ryotsu
http://api.openweathermap.org/data/2.5/weather?appid=cd80ea31f0dcfaa9dffb1cd446d9a99b&q=ryotsu
Processing Record 13| Uvira
http://api.openweathermap.org/data/2.5/weather?appid=cd80ea31f0dcfaa9dffb1cd446d9a99b&q=uvira
Processing Record 14| Mpika
http://api.openweathermap.org/data/2.5/weather?appid=cd80ea31f0dcfaa9dffb1cd446d9a99b&q=mpika
Processing Record 15| Menongue
http://api.openweathermap.org/data/2.5/weather?appid=cd80ea31f0dcfaa9dffb1cd446d9a99b&q=menongue
Processing Record 16| Muroto
http://api.openweathermap.org/data/2.5/weather?appid=cd80ea31f0dcfaa9dffb1cd446d9a99b&q=muroto
Processing Record 17| Sabha
http://api.openweathermap.org/data/2.5/weather?appid=cd80ea31f0dcfaa9dffb1cd446d9a99b&q=sabha
Processing Record 18| Taltal
http://api.openweathermap.org/data/2.5/weather?appid=cd80ea31f0dcfaa9dffb1cd446d9a99b&q=taltal
Processing Record 19| Daru
http://api.openweathermap.org/data/2.5/weather?appid=cd80ea31f0dcfaa9dffb1cd446d9a99b&q=daru
Processing Record 20| Ploemeur
http://api.openweathermap.org/data/2.5/weather?appid=cd80ea31f0dcfaa9dffb1cd446d9a99b&q=ploemeur
Processing Record 21| Port Elizabeth
http://api.openweathermap.org/data/2.5/weather?appid=cd80ea31f0dcfaa9dffb1cd446d9a99b&q=port%20elizabeth
Processing Record 22| Albany
http://api.openweathermap.org/data/2.5/weather?appid=cd80ea31f0dcfaa9dffb1cd446d9a99b&q=albany
city not found ... skipping 
Processing Record 23| Cidreira
http://api.openweathermap.org/data/2.5/weather?appid=cd80ea31f0dcfaa9dffb1cd446d9a99b&q=cidreira
Processing Record 24| Nikolskoye
http://api.openweathermap.org/data/2.5/weather?appid=cd80ea31f0dcfaa9dffb1cd446d9a99b&q=nikolskoye
Processing Record 25| Hobart
http://api.openweathermap.org/data/2.5/weather?appid=cd80ea31f0dcfaa9dffb1cd446d9a99b&q=hobart
Processing Record 26| Huilong
http://api.openweathermap.org/data/2.5/weather?appid=cd80ea31f0dcfaa9dffb1cd446d9a99b&q=huilong
Processing Record 27| San Policarpo
http://api.openweathermap.org/data/2.5/weather?appid=cd80ea31f0dcfaa9dffb1cd446d9a99b&q=san%20policarpo
Processing Record 28| Vestmannaeyjar
http://api.openweathermap.org/data/2.5/weather?appid=cd80ea31f0dcfaa9dffb1cd446d9a99b&q=vestmannaeyjar
city not found ... skipping 
Processing Record 29| Lompoc
http://api.openweathermap.org/data/2.5/weather?appid=cd80ea31f0dcfaa9dffb1cd446d9a99b&q=lompoc
Processing Record 30| Hithadhoo
http://api.openweathermap.org/data/2.5/weather?appid=cd80ea31f0dcfaa9dffb1cd446d9a99b&q=hithadhoo
Processing Record 31| Los Llanos de Aridane
http://api.openweathermap.org/data/2.5/weather?appid=cd80ea31f0dcfaa9dffb1cd446d9a99b&q=los%20llanos%20de%20aridane
Processing Record 32| Qaanaaq
http://api.openweathermap.org/data/2.5/weather?appid=cd80ea31f0dcfaa9dffb1cd446d9a99b&q=qaanaaq
Processing Record 33| Buarcos
http://api.openweathermap.org/data/2.5/weather?appid=cd80ea31f0dcfaa9dffb1cd446d9a99b&q=buarcos
Processing Record 34| Najran
http://api.openweathermap.org/data/2.5/weather?appid=cd80ea31f0dcfaa9dffb1cd446d9a99b&q=najran
Processing Record 35| Dunedin
http://api.openweathermap.org/data/2.5/weather?appid=cd80ea31f0dcfaa9dffb1cd446d9a99b&q=dunedin
Processing Record 36| Talara
http://api.openweathermap.org/data/2.5/weather?appid=cd80ea31f0dcfaa9dffb1cd446d9a99b&q=talara
Processing Record 37| Puerto Ayora
http://api.openweathermap.org/data/2.5/weather?appid=cd80ea31f0dcfaa9dffb1cd446d9a99b&q=puerto%20ayora
Processing Record 38| Pisco
http://api.openweathermap.org/data/2.5/weather?appid=cd80ea31f0dcfaa9dffb1cd446d9a99b&q=pisco
Processing Record 39| Mayo
http://api.openweathermap.org/data/2.5/weather?appid=cd80ea31f0dcfaa9dffb1cd446d9a99b&q=mayo
Processing Record 40| Richards Bay
http://api.openweathermap.org/data/2.5/weather?appid=cd80ea31f0dcfaa9dffb1cd446d9a99b&q=richards%20bay
Processing Record 41| Kaolinovo
http://api.openweathermap.org/data/2.5/weather?appid=cd80ea31f0dcfaa9dffb1cd446d9a99b&q=kaolinovo
city not found ... skipping 
Processing Record 42| Esperance
http://api.openweathermap.org/data/2.5/weather?appid=cd80ea31f0dcfaa9dffb1cd446d9a99b&q=esperance
Processing Record 43| Invermere
http://api.openweathermap.org/data/2.5/weather?appid=cd80ea31f0dcfaa9dffb1cd446d9a99b&q=invermere
Processing Record 44| Rikitea
http://api.openweathermap.org/data/2.5/weather?appid=cd80ea31f0dcfaa9dffb1cd446d9a99b&q=rikitea
Processing Record 45| Port Hedland
http://api.openweathermap.org/data/2.5/weather?appid=cd80ea31f0dcfaa9dffb1cd446d9a99b&q=port%20hedland
Processing Record 46| Saldanha
http://api.openweathermap.org/data/2.5/weather?appid=cd80ea31f0dcfaa9dffb1cd446d9a99b&q=saldanha
Processing Record 47| New Norfolk
http://api.openweathermap.org/data/2.5/weather?appid=cd80ea31f0dcfaa9dffb1cd446d9a99b&q=new%20norfolk
Processing Record 48| Doka
http://api.openweathermap.org/data/2.5/weather?appid=cd80ea31f0dcfaa9dffb1cd446d9a99b&q=doka
Processing Record 49| Cape Town
http://api.openweathermap.org/data/2.5/weather?appid=cd80ea31f0dcfaa9dffb1cd446d9a99b&q=cape%20town
city not found ... skipping 
Processing Record 50| Iwanai
http://api.openweathermap.org/data/2.5/weather?appid=cd80ea31f0dcfaa9dffb1cd446d9a99b&q=iwanai
Processing Record 51| Bluff
http://api.openweathermap.org/data/2.5/weather?appid=cd80ea31f0dcfaa9dffb1cd446d9a99b&q=bluff
Processing Record 52| Yellowknife
http://api.openweathermap.org/data/2.5/weather?appid=cd80ea31f0dcfaa9dffb1cd446d9a99b&q=yellowknife
Processing Record 53| Horadiz
http://api.openweathermap.org/data/2.5/weather?appid=cd80ea31f0dcfaa9dffb1cd446d9a99b&q=horadiz
Processing Record 54| San Patricio
http://api.openweathermap.org/data/2.5/weather?appid=cd80ea31f0dcfaa9dffb1cd446d9a99b&q=san%20patricio
Processing Record 55| Saint George
http://api.openweathermap.org/data/2.5/weather?appid=cd80ea31f0dcfaa9dffb1cd446d9a99b&q=saint%20george
Processing Record 56| Saint-Philippe
http://api.openweathermap.org/data/2.5/weather?appid=cd80ea31f0dcfaa9dffb1cd446d9a99b&q=saint-philippe
Processing Record 57| Codrington
http://api.openweathermap.org/data/2.5/weather?appid=cd80ea31f0dcfaa9dffb1cd446d9a99b&q=codrington
Processing Record 58| Tautira
http://api.openweathermap.org/data/2.5/weather?appid=cd80ea31f0dcfaa9dffb1cd446d9a99b&q=tautira
Processing Record 59| Valdivia
http://api.openweathermap.org/data/2.5/weather?appid=cd80ea31f0dcfaa9dffb1cd446d9a99b&q=valdivia
Processing Record 60| Jumla
http://api.openweathermap.org/data/2.5/weather?appid=cd80ea31f0dcfaa9dffb1cd446d9a99b&q=jumla
Processing Record 61| Hambantota
http://api.openweathermap.org/data/2.5/weather?appid=cd80ea31f0dcfaa9dffb1cd446d9a99b&q=hambantota
Processing Record 62| Dali
http://api.openweathermap.org/data/2.5/weather?appid=cd80ea31f0dcfaa9dffb1cd446d9a99b&q=dali
Processing Record 63| Sao Joao da Barra
http://api.openweathermap.org/data/2.5/weather?appid=cd80ea31f0dcfaa9dffb1cd446d9a99b&q=sao%20joao%20da%20barra
Processing Record 64| Ternate
http://api.openweathermap.org/data/2.5/weather?appid=cd80ea31f0dcfaa9dffb1cd446d9a99b&q=ternate
Processing Record 65| Belyy Yar
http://api.openweathermap.org/data/2.5/weather?appid=cd80ea31f0dcfaa9dffb1cd446d9a99b&q=belyy%20yar
city not found ... skipping 
Processing Record 66| Vaini
http://api.openweathermap.org/data/2.5/weather?appid=cd80ea31f0dcfaa9dffb1cd446d9a99b&q=vaini
Processing Record 67| Berdigestyakh
http://api.openweathermap.org/data/2.5/weather?appid=cd80ea31f0dcfaa9dffb1cd446d9a99b&q=berdigestyakh
city not found ... skipping 
Processing Record 68| Darhan
http://api.openweathermap.org/data/2.5/weather?appid=cd80ea31f0dcfaa9dffb1cd446d9a99b&q=darhan
city not found ... skipping 
city not found ... skipping 
Processing Record 69| Ribeira Grande
http://api.openweathermap.org/data/2.5/weather?appid=cd80ea31f0dcfaa9dffb1cd446d9a99b&q=ribeira%20grande
Processing Record 70| Kommunar
http://api.openweathermap.org/data/2.5/weather?appid=cd80ea31f0dcfaa9dffb1cd446d9a99b&q=kommunar
Processing Record 71| Tilichiki
http://api.openweathermap.org/data/2.5/weather?appid=cd80ea31f0dcfaa9dffb1cd446d9a99b&q=tilichiki
Processing Record 72| Kindu
http://api.openweathermap.org/data/2.5/weather?appid=cd80ea31f0dcfaa9dffb1cd446d9a99b&q=kindu
Processing Record 73| Tasiilaq
http://api.openweathermap.org/data/2.5/weather?appid=cd80ea31f0dcfaa9dffb1cd446d9a99b&q=tasiilaq
Processing Record 74| Barrow
http://api.openweathermap.org/data/2.5/weather?appid=cd80ea31f0dcfaa9dffb1cd446d9a99b&q=barrow
Processing Record 75| Comodoro Rivadavia
http://api.openweathermap.org/data/2.5/weather?appid=cd80ea31f0dcfaa9dffb1cd446d9a99b&q=comodoro%20rivadavia
Processing Record 76| Isangel
http://api.openweathermap.org/data/2.5/weather?appid=cd80ea31f0dcfaa9dffb1cd446d9a99b&q=isangel
Processing Record 77| Honningsvag
http://api.openweathermap.org/data/2.5/weather?appid=cd80ea31f0dcfaa9dffb1cd446d9a99b&q=honningsvag
Processing Record 78| Jamestown
http://api.openweathermap.org/data/2.5/weather?appid=cd80ea31f0dcfaa9dffb1cd446d9a99b&q=jamestown
Processing Record 79| Qaqortoq
http://api.openweathermap.org/data/2.5/weather?appid=cd80ea31f0dcfaa9dffb1cd446d9a99b&q=qaqortoq
Processing Record 80| Adrar
http://api.openweathermap.org/data/2.5/weather?appid=cd80ea31f0dcfaa9dffb1cd446d9a99b&q=adrar
Processing Record 81| Hilo
http://api.openweathermap.org/data/2.5/weather?appid=cd80ea31f0dcfaa9dffb1cd446d9a99b&q=hilo
Processing Record 82| Dwarka
http://api.openweathermap.org/data/2.5/weather?appid=cd80ea31f0dcfaa9dffb1cd446d9a99b&q=dwarka
Processing Record 83| Yulin
http://api.openweathermap.org/data/2.5/weather?appid=cd80ea31f0dcfaa9dffb1cd446d9a99b&q=yulin
Processing Record 84| Dudinka
http://api.openweathermap.org/data/2.5/weather?appid=cd80ea31f0dcfaa9dffb1cd446d9a99b&q=dudinka
Processing Record 85| Coquimbo
http://api.openweathermap.org/data/2.5/weather?appid=cd80ea31f0dcfaa9dffb1cd446d9a99b&q=coquimbo
Processing Record 86| Broome
http://api.openweathermap.org/data/2.5/weather?appid=cd80ea31f0dcfaa9dffb1cd446d9a99b&q=broome
Processing Record 87| Atuona
http://api.openweathermap.org/data/2.5/weather?appid=cd80ea31f0dcfaa9dffb1cd446d9a99b&q=atuona
Processing Record 88| Avarua
http://api.openweathermap.org/data/2.5/weather?appid=cd80ea31f0dcfaa9dffb1cd446d9a99b&q=avarua
Processing Record 89| Marfino
http://api.openweathermap.org/data/2.5/weather?appid=cd80ea31f0dcfaa9dffb1cd446d9a99b&q=marfino
Processing Record 90| Cabo San Lucas
http://api.openweathermap.org/data/2.5/weather?appid=cd80ea31f0dcfaa9dffb1cd446d9a99b&q=cabo%20san%20lucas
city not found ... skipping 
Processing Record 91| Voh
http://api.openweathermap.org/data/2.5/weather?appid=cd80ea31f0dcfaa9dffb1cd446d9a99b&q=voh
Processing Record 92| Ahipara
http://api.openweathermap.org/data/2.5/weather?appid=cd80ea31f0dcfaa9dffb1cd446d9a99b&q=ahipara
Processing Record 93| Kachug
http://api.openweathermap.org/data/2.5/weather?appid=cd80ea31f0dcfaa9dffb1cd446d9a99b&q=kachug
Processing Record 94| Alekseyevskaya
http://api.openweathermap.org/data/2.5/weather?appid=cd80ea31f0dcfaa9dffb1cd446d9a99b&q=alekseyevskaya
city not found ... skipping 
Processing Record 95| Tuktoyaktuk
http://api.openweathermap.org/data/2.5/weather?appid=cd80ea31f0dcfaa9dffb1cd446d9a99b&q=tuktoyaktuk
Processing Record 96| East London
http://api.openweathermap.org/data/2.5/weather?appid=cd80ea31f0dcfaa9dffb1cd446d9a99b&q=east%20london
city not found ... skipping 
Processing Record 97| Lagoa
http://api.openweathermap.org/data/2.5/weather?appid=cd80ea31f0dcfaa9dffb1cd446d9a99b&q=lagoa
Processing Record 98| Xining
http://api.openweathermap.org/data/2.5/weather?appid=cd80ea31f0dcfaa9dffb1cd446d9a99b&q=xining
Processing Record 99| Ippy
http://api.openweathermap.org/data/2.5/weather?appid=cd80ea31f0dcfaa9dffb1cd446d9a99b&q=ippy
Processing Record 100| Pevek
http://api.openweathermap.org/data/2.5/weather?appid=cd80ea31f0dcfaa9dffb1cd446d9a99b&q=pevek
city not found ... skipping 
Processing Record 101| Ust-Kuyga
http://api.openweathermap.org/data/2.5/weather?appid=cd80ea31f0dcfaa9dffb1cd446d9a99b&q=ust-kuyga
Processing Record 102| Arrifes
http://api.openweathermap.org/data/2.5/weather?appid=cd80ea31f0dcfaa9dffb1cd446d9a99b&q=arrifes
Processing Record 103| Poyarkovo
http://api.openweathermap.org/data/2.5/weather?appid=cd80ea31f0dcfaa9dffb1cd446d9a99b&q=poyarkovo
Processing Record 104| Haines Junction
http://api.openweathermap.org/data/2.5/weather?appid=cd80ea31f0dcfaa9dffb1cd446d9a99b&q=haines%20junction
Processing Record 105| Bukachacha
http://api.openweathermap.org/data/2.5/weather?appid=cd80ea31f0dcfaa9dffb1cd446d9a99b&q=bukachacha
Processing Record 106| Felanitx
http://api.openweathermap.org/data/2.5/weather?appid=cd80ea31f0dcfaa9dffb1cd446d9a99b&q=felanitx
city not found ... skipping 
Processing Record 107| Carnarvon
http://api.openweathermap.org/data/2.5/weather?appid=cd80ea31f0dcfaa9dffb1cd446d9a99b&q=carnarvon
Processing Record 108| Verkhoyansk
http://api.openweathermap.org/data/2.5/weather?appid=cd80ea31f0dcfaa9dffb1cd446d9a99b&q=verkhoyansk
Processing Record 109| Kodiak
http://api.openweathermap.org/data/2.5/weather?appid=cd80ea31f0dcfaa9dffb1cd446d9a99b&q=kodiak
Processing Record 110| Umm Lajj
http://api.openweathermap.org/data/2.5/weather?appid=cd80ea31f0dcfaa9dffb1cd446d9a99b&q=umm%20lajj
Processing Record 111| Freistadt
http://api.openweathermap.org/data/2.5/weather?appid=cd80ea31f0dcfaa9dffb1cd446d9a99b&q=freistadt
city not found ... skipping 
Processing Record 112| Bubaque
http://api.openweathermap.org/data/2.5/weather?appid=cd80ea31f0dcfaa9dffb1cd446d9a99b&q=bubaque
Processing Record 113| Lishui
http://api.openweathermap.org/data/2.5/weather?appid=cd80ea31f0dcfaa9dffb1cd446d9a99b&q=lishui
Processing Record 114| Baruun-Urt
http://api.openweathermap.org/data/2.5/weather?appid=cd80ea31f0dcfaa9dffb1cd446d9a99b&q=baruun-urt
Processing Record 115| Thompson
http://api.openweathermap.org/data/2.5/weather?appid=cd80ea31f0dcfaa9dffb1cd446d9a99b&q=thompson
Processing Record 116| Mahebourg
http://api.openweathermap.org/data/2.5/weather?appid=cd80ea31f0dcfaa9dffb1cd446d9a99b&q=mahebourg
Processing Record 117| Kharan
http://api.openweathermap.org/data/2.5/weather?appid=cd80ea31f0dcfaa9dffb1cd446d9a99b&q=kharan
Processing Record 118| Port Alfred
http://api.openweathermap.org/data/2.5/weather?appid=cd80ea31f0dcfaa9dffb1cd446d9a99b&q=port%20alfred
Processing Record 119| Merauke
http://api.openweathermap.org/data/2.5/weather?appid=cd80ea31f0dcfaa9dffb1cd446d9a99b&q=merauke
Processing Record 120| Nome
http://api.openweathermap.org/data/2.5/weather?appid=cd80ea31f0dcfaa9dffb1cd446d9a99b&q=nome
Processing Record 121| Mandurah
http://api.openweathermap.org/data/2.5/weather?appid=cd80ea31f0dcfaa9dffb1cd446d9a99b&q=mandurah
Processing Record 122| Muzhi
http://api.openweathermap.org/data/2.5/weather?appid=cd80ea31f0dcfaa9dffb1cd446d9a99b&q=muzhi
Processing Record 123| Kapaa
http://api.openweathermap.org/data/2.5/weather?appid=cd80ea31f0dcfaa9dffb1cd446d9a99b&q=kapaa
Processing Record 124| Shingu
http://api.openweathermap.org/data/2.5/weather?appid=cd80ea31f0dcfaa9dffb1cd446d9a99b&q=shingu
Processing Record 125| Tignere
http://api.openweathermap.org/data/2.5/weather?appid=cd80ea31f0dcfaa9dffb1cd446d9a99b&q=tignere
Processing Record 126| Cherskiy
http://api.openweathermap.org/data/2.5/weather?appid=cd80ea31f0dcfaa9dffb1cd446d9a99b&q=cherskiy
Processing Record 127| Fortuna
http://api.openweathermap.org/data/2.5/weather?appid=cd80ea31f0dcfaa9dffb1cd446d9a99b&q=fortuna
Processing Record 128| Giyani
http://api.openweathermap.org/data/2.5/weather?appid=cd80ea31f0dcfaa9dffb1cd446d9a99b&q=giyani
city not found ... skipping 
Processing Record 129| Yuzhno-Kurilsk
http://api.openweathermap.org/data/2.5/weather?appid=cd80ea31f0dcfaa9dffb1cd446d9a99b&q=yuzhno-kurilsk
Processing Record 130| Orange
http://api.openweathermap.org/data/2.5/weather?appid=cd80ea31f0dcfaa9dffb1cd446d9a99b&q=orange
Processing Record 131| Muros
http://api.openweathermap.org/data/2.5/weather?appid=cd80ea31f0dcfaa9dffb1cd446d9a99b&q=muros
Processing Record 132| Kendal
http://api.openweathermap.org/data/2.5/weather?appid=cd80ea31f0dcfaa9dffb1cd446d9a99b&q=kendal
Processing Record 133| Kieta
http://api.openweathermap.org/data/2.5/weather?appid=cd80ea31f0dcfaa9dffb1cd446d9a99b&q=kieta
Processing Record 134| Kropotkin
http://api.openweathermap.org/data/2.5/weather?appid=cd80ea31f0dcfaa9dffb1cd446d9a99b&q=kropotkin
Processing Record 135| Makakilo City
http://api.openweathermap.org/data/2.5/weather?appid=cd80ea31f0dcfaa9dffb1cd446d9a99b&q=makakilo%20city
Processing Record 136| Mitsamiouli
http://api.openweathermap.org/data/2.5/weather?appid=cd80ea31f0dcfaa9dffb1cd446d9a99b&q=mitsamiouli
Processing Record 137| Burnie
http://api.openweathermap.org/data/2.5/weather?appid=cd80ea31f0dcfaa9dffb1cd446d9a99b&q=burnie
Processing Record 138| Antalaha
http://api.openweathermap.org/data/2.5/weather?appid=cd80ea31f0dcfaa9dffb1cd446d9a99b&q=antalaha
Processing Record 139| Usinsk
http://api.openweathermap.org/data/2.5/weather?appid=cd80ea31f0dcfaa9dffb1cd446d9a99b&q=usinsk
Processing Record 140| Longyearbyen
http://api.openweathermap.org/data/2.5/weather?appid=cd80ea31f0dcfaa9dffb1cd446d9a99b&q=longyearbyen
Processing Record 141| Grand Gaube
http://api.openweathermap.org/data/2.5/weather?appid=cd80ea31f0dcfaa9dffb1cd446d9a99b&q=grand%20gaube
Processing Record 142| Talwara
http://api.openweathermap.org/data/2.5/weather?appid=cd80ea31f0dcfaa9dffb1cd446d9a99b&q=talwara
Processing Record 143| Henties Bay
http://api.openweathermap.org/data/2.5/weather?appid=cd80ea31f0dcfaa9dffb1cd446d9a99b&q=henties%20bay
Processing Record 144| Faanui
http://api.openweathermap.org/data/2.5/weather?appid=cd80ea31f0dcfaa9dffb1cd446d9a99b&q=faanui
Processing Record 145| Georgetown
http://api.openweathermap.org/data/2.5/weather?appid=cd80ea31f0dcfaa9dffb1cd446d9a99b&q=georgetown
city not found ... skipping 
city not found ... skipping 
city not found ... skipping 
Processing Record 146| Mount Gambier
http://api.openweathermap.org/data/2.5/weather?appid=cd80ea31f0dcfaa9dffb1cd446d9a99b&q=mount%20gambier
Processing Record 147| Seia
http://api.openweathermap.org/data/2.5/weather?appid=cd80ea31f0dcfaa9dffb1cd446d9a99b&q=seia
Processing Record 148| San Carlos de Bariloche
http://api.openweathermap.org/data/2.5/weather?appid=cd80ea31f0dcfaa9dffb1cd446d9a99b&q=san%20carlos%20de%20bariloche
Processing Record 149| Northam
http://api.openweathermap.org/data/2.5/weather?appid=cd80ea31f0dcfaa9dffb1cd446d9a99b&q=northam
Processing Record 150| Avera
http://api.openweathermap.org/data/2.5/weather?appid=cd80ea31f0dcfaa9dffb1cd446d9a99b&q=avera
city not found ... skipping 
Processing Record 151| Karratha
http://api.openweathermap.org/data/2.5/weather?appid=cd80ea31f0dcfaa9dffb1cd446d9a99b&q=karratha
Processing Record 152| Lerwick
http://api.openweathermap.org/data/2.5/weather?appid=cd80ea31f0dcfaa9dffb1cd446d9a99b&q=lerwick
city not found ... skipping 
Processing Record 153| Atambua
http://api.openweathermap.org/data/2.5/weather?appid=cd80ea31f0dcfaa9dffb1cd446d9a99b&q=atambua
Processing Record 154| Severo-Kurilsk
http://api.openweathermap.org/data/2.5/weather?appid=cd80ea31f0dcfaa9dffb1cd446d9a99b&q=severo-kurilsk
Processing Record 155| Dikson
http://api.openweathermap.org/data/2.5/weather?appid=cd80ea31f0dcfaa9dffb1cd446d9a99b&q=dikson
Processing Record 156| Alta Floresta
http://api.openweathermap.org/data/2.5/weather?appid=cd80ea31f0dcfaa9dffb1cd446d9a99b&q=alta%20floresta
Processing Record 157| Cukai
http://api.openweathermap.org/data/2.5/weather?appid=cd80ea31f0dcfaa9dffb1cd446d9a99b&q=cukai
Processing Record 158| Medford
http://api.openweathermap.org/data/2.5/weather?appid=cd80ea31f0dcfaa9dffb1cd446d9a99b&q=medford
city not found ... skipping 
Processing Record 159| Geraldton
http://api.openweathermap.org/data/2.5/weather?appid=cd80ea31f0dcfaa9dffb1cd446d9a99b&q=geraldton
Processing Record 160| Ukiah
http://api.openweathermap.org/data/2.5/weather?appid=cd80ea31f0dcfaa9dffb1cd446d9a99b&q=ukiah
Processing Record 161| Naze
http://api.openweathermap.org/data/2.5/weather?appid=cd80ea31f0dcfaa9dffb1cd446d9a99b&q=naze
Processing Record 162| Talnakh
http://api.openweathermap.org/data/2.5/weather?appid=cd80ea31f0dcfaa9dffb1cd446d9a99b&q=talnakh
Processing Record 163| Tabas
http://api.openweathermap.org/data/2.5/weather?appid=cd80ea31f0dcfaa9dffb1cd446d9a99b&q=tabas
Processing Record 164| Saint-Pierre
http://api.openweathermap.org/data/2.5/weather?appid=cd80ea31f0dcfaa9dffb1cd446d9a99b&q=saint-pierre
Processing Record 165| Sur
http://api.openweathermap.org/data/2.5/weather?appid=cd80ea31f0dcfaa9dffb1cd446d9a99b&q=sur
Processing Record 166| Ixtapa
http://api.openweathermap.org/data/2.5/weather?appid=cd80ea31f0dcfaa9dffb1cd446d9a99b&q=ixtapa
Processing Record 167| Saint Cloud
http://api.openweathermap.org/data/2.5/weather?appid=cd80ea31f0dcfaa9dffb1cd446d9a99b&q=saint%20cloud
Processing Record 168| Karlovac
http://api.openweathermap.org/data/2.5/weather?appid=cd80ea31f0dcfaa9dffb1cd446d9a99b&q=karlovac
Processing Record 169| Urusha
http://api.openweathermap.org/data/2.5/weather?appid=cd80ea31f0dcfaa9dffb1cd446d9a99b&q=urusha
Processing Record 170| Tura
http://api.openweathermap.org/data/2.5/weather?appid=cd80ea31f0dcfaa9dffb1cd446d9a99b&q=tura
Processing Record 171| Yibin
http://api.openweathermap.org/data/2.5/weather?appid=cd80ea31f0dcfaa9dffb1cd446d9a99b&q=yibin
Processing Record 172| Leningradskiy
http://api.openweathermap.org/data/2.5/weather?appid=cd80ea31f0dcfaa9dffb1cd446d9a99b&q=leningradskiy
Processing Record 173| Flinders
http://api.openweathermap.org/data/2.5/weather?appid=cd80ea31f0dcfaa9dffb1cd446d9a99b&q=flinders
Processing Record 174| Castro
http://api.openweathermap.org/data/2.5/weather?appid=cd80ea31f0dcfaa9dffb1cd446d9a99b&q=castro
Processing Record 175| Inuvik
http://api.openweathermap.org/data/2.5/weather?appid=cd80ea31f0dcfaa9dffb1cd446d9a99b&q=inuvik
Processing Record 176| Bowmore
http://api.openweathermap.org/data/2.5/weather?appid=cd80ea31f0dcfaa9dffb1cd446d9a99b&q=bowmore
Processing Record 177| Yar-Sale
http://api.openweathermap.org/data/2.5/weather?appid=cd80ea31f0dcfaa9dffb1cd446d9a99b&q=yar-sale
city not found ... skipping 
Processing Record 178| Gorom-Gorom
http://api.openweathermap.org/data/2.5/weather?appid=cd80ea31f0dcfaa9dffb1cd446d9a99b&q=gorom-gorom
Processing Record 179| Biak
http://api.openweathermap.org/data/2.5/weather?appid=cd80ea31f0dcfaa9dffb1cd446d9a99b&q=biak
Processing Record 180| Anadyr
http://api.openweathermap.org/data/2.5/weather?appid=cd80ea31f0dcfaa9dffb1cd446d9a99b&q=anadyr
Processing Record 181| Hermiston
http://api.openweathermap.org/data/2.5/weather?appid=cd80ea31f0dcfaa9dffb1cd446d9a99b&q=hermiston
Processing Record 182| Cap Malheureux
http://api.openweathermap.org/data/2.5/weather?appid=cd80ea31f0dcfaa9dffb1cd446d9a99b&q=cap%20malheureux
Processing Record 183| Barra Velha
http://api.openweathermap.org/data/2.5/weather?appid=cd80ea31f0dcfaa9dffb1cd446d9a99b&q=barra%20velha
Processing Record 184| Zhigansk
http://api.openweathermap.org/data/2.5/weather?appid=cd80ea31f0dcfaa9dffb1cd446d9a99b&q=zhigansk
Processing Record 185| Hamilton
http://api.openweathermap.org/data/2.5/weather?appid=cd80ea31f0dcfaa9dffb1cd446d9a99b&q=hamilton
Processing Record 186| Maracaibo
http://api.openweathermap.org/data/2.5/weather?appid=cd80ea31f0dcfaa9dffb1cd446d9a99b&q=maracaibo
Processing Record 187| Marsh Harbour
http://api.openweathermap.org/data/2.5/weather?appid=cd80ea31f0dcfaa9dffb1cd446d9a99b&q=marsh%20harbour
Processing Record 188| Manokwari
http://api.openweathermap.org/data/2.5/weather?appid=cd80ea31f0dcfaa9dffb1cd446d9a99b&q=manokwari
Processing Record 189| Homer
http://api.openweathermap.org/data/2.5/weather?appid=cd80ea31f0dcfaa9dffb1cd446d9a99b&q=homer
Processing Record 190| Vila Velha
http://api.openweathermap.org/data/2.5/weather?appid=cd80ea31f0dcfaa9dffb1cd446d9a99b&q=vila%20velha
Processing Record 191| Hami
http://api.openweathermap.org/data/2.5/weather?appid=cd80ea31f0dcfaa9dffb1cd446d9a99b&q=hami
Processing Record 192| Acapulco
http://api.openweathermap.org/data/2.5/weather?appid=cd80ea31f0dcfaa9dffb1cd446d9a99b&q=acapulco
Processing Record 193| Hasaki
http://api.openweathermap.org/data/2.5/weather?appid=cd80ea31f0dcfaa9dffb1cd446d9a99b&q=hasaki
Processing Record 194| Chuy
http://api.openweathermap.org/data/2.5/weather?appid=cd80ea31f0dcfaa9dffb1cd446d9a99b&q=chuy
Processing Record 195| Iqaluit
http://api.openweathermap.org/data/2.5/weather?appid=cd80ea31f0dcfaa9dffb1cd446d9a99b&q=iqaluit
Processing Record 196| Yuanping
http://api.openweathermap.org/data/2.5/weather?appid=cd80ea31f0dcfaa9dffb1cd446d9a99b&q=yuanping
Processing Record 197| Poum
http://api.openweathermap.org/data/2.5/weather?appid=cd80ea31f0dcfaa9dffb1cd446d9a99b&q=poum
Processing Record 198| Yumen
http://api.openweathermap.org/data/2.5/weather?appid=cd80ea31f0dcfaa9dffb1cd446d9a99b&q=yumen
Processing Record 199| Ende
http://api.openweathermap.org/data/2.5/weather?appid=cd80ea31f0dcfaa9dffb1cd446d9a99b&q=ende
Processing Record 200| Cockburn Town
http://api.openweathermap.org/data/2.5/weather?appid=cd80ea31f0dcfaa9dffb1cd446d9a99b&q=cockburn%20town
city not found ... skipping 
Processing Record 201| Mar del Plata
http://api.openweathermap.org/data/2.5/weather?appid=cd80ea31f0dcfaa9dffb1cd446d9a99b&q=mar%20del%20plata
Processing Record 202| Narsaq
http://api.openweathermap.org/data/2.5/weather?appid=cd80ea31f0dcfaa9dffb1cd446d9a99b&q=narsaq
Processing Record 203| Eftimie Murgu
http://api.openweathermap.org/data/2.5/weather?appid=cd80ea31f0dcfaa9dffb1cd446d9a99b&q=eftimie%20murgu
Processing Record 204| Xichang
http://api.openweathermap.org/data/2.5/weather?appid=cd80ea31f0dcfaa9dffb1cd446d9a99b&q=xichang
Processing Record 205| Lesogorsk
http://api.openweathermap.org/data/2.5/weather?appid=cd80ea31f0dcfaa9dffb1cd446d9a99b&q=lesogorsk
Processing Record 206| Butaritari
http://api.openweathermap.org/data/2.5/weather?appid=cd80ea31f0dcfaa9dffb1cd446d9a99b&q=butaritari
Processing Record 207| Marystown
http://api.openweathermap.org/data/2.5/weather?appid=cd80ea31f0dcfaa9dffb1cd446d9a99b&q=marystown
Processing Record 208| Indianola
http://api.openweathermap.org/data/2.5/weather?appid=cd80ea31f0dcfaa9dffb1cd446d9a99b&q=indianola
Processing Record 209| Mandera
http://api.openweathermap.org/data/2.5/weather?appid=cd80ea31f0dcfaa9dffb1cd446d9a99b&q=mandera
Processing Record 210| Nanortalik
http://api.openweathermap.org/data/2.5/weather?appid=cd80ea31f0dcfaa9dffb1cd446d9a99b&q=nanortalik
city not found ... skipping 
Processing Record 211| Lavrentiya
http://api.openweathermap.org/data/2.5/weather?appid=cd80ea31f0dcfaa9dffb1cd446d9a99b&q=lavrentiya
Processing Record 212| Taitung
http://api.openweathermap.org/data/2.5/weather?appid=cd80ea31f0dcfaa9dffb1cd446d9a99b&q=taitung
Processing Record 213| Satka
http://api.openweathermap.org/data/2.5/weather?appid=cd80ea31f0dcfaa9dffb1cd446d9a99b&q=satka
city not found ... skipping 
Processing Record 214| Quatre Cocos
http://api.openweathermap.org/data/2.5/weather?appid=cd80ea31f0dcfaa9dffb1cd446d9a99b&q=quatre%20cocos
Processing Record 215| Provideniya
http://api.openweathermap.org/data/2.5/weather?appid=cd80ea31f0dcfaa9dffb1cd446d9a99b&q=provideniya
Processing Record 216| Constitucion
http://api.openweathermap.org/data/2.5/weather?appid=cd80ea31f0dcfaa9dffb1cd446d9a99b&q=constitucion
Processing Record 217| Victoria
http://api.openweathermap.org/data/2.5/weather?appid=cd80ea31f0dcfaa9dffb1cd446d9a99b&q=victoria
Processing Record 218| Bambous Virieux
http://api.openweathermap.org/data/2.5/weather?appid=cd80ea31f0dcfaa9dffb1cd446d9a99b&q=bambous%20virieux
Processing Record 219| Port Macquarie
http://api.openweathermap.org/data/2.5/weather?appid=cd80ea31f0dcfaa9dffb1cd446d9a99b&q=port%20macquarie
Processing Record 220| Sao Filipe
http://api.openweathermap.org/data/2.5/weather?appid=cd80ea31f0dcfaa9dffb1cd446d9a99b&q=sao%20filipe
Processing Record 221| Ust-Kut
http://api.openweathermap.org/data/2.5/weather?appid=cd80ea31f0dcfaa9dffb1cd446d9a99b&q=ust-kut
Processing Record 222| Guerrero Negro
http://api.openweathermap.org/data/2.5/weather?appid=cd80ea31f0dcfaa9dffb1cd446d9a99b&q=guerrero%20negro
Processing Record 223| Gainesville
http://api.openweathermap.org/data/2.5/weather?appid=cd80ea31f0dcfaa9dffb1cd446d9a99b&q=gainesville
Processing Record 224| Bredasdorp
http://api.openweathermap.org/data/2.5/weather?appid=cd80ea31f0dcfaa9dffb1cd446d9a99b&q=bredasdorp
Processing Record 225| Orange Cove
http://api.openweathermap.org/data/2.5/weather?appid=cd80ea31f0dcfaa9dffb1cd446d9a99b&q=orange%20cove
Processing Record 226| Ilulissat
http://api.openweathermap.org/data/2.5/weather?appid=cd80ea31f0dcfaa9dffb1cd446d9a99b&q=ilulissat
Processing Record 227| Lesnoy
http://api.openweathermap.org/data/2.5/weather?appid=cd80ea31f0dcfaa9dffb1cd446d9a99b&q=lesnoy
Processing Record 228| Sitka
http://api.openweathermap.org/data/2.5/weather?appid=cd80ea31f0dcfaa9dffb1cd446d9a99b&q=sitka
Processing Record 229| Elat
http://api.openweathermap.org/data/2.5/weather?appid=cd80ea31f0dcfaa9dffb1cd446d9a99b&q=elat
Processing Record 230| San Quintin
http://api.openweathermap.org/data/2.5/weather?appid=cd80ea31f0dcfaa9dffb1cd446d9a99b&q=san%20quintin
city not found ... skipping 
Processing Record 231| Alofi
http://api.openweathermap.org/data/2.5/weather?appid=cd80ea31f0dcfaa9dffb1cd446d9a99b&q=alofi
Processing Record 232| Xixiang
http://api.openweathermap.org/data/2.5/weather?appid=cd80ea31f0dcfaa9dffb1cd446d9a99b&q=xixiang
Processing Record 233| Uray
http://api.openweathermap.org/data/2.5/weather?appid=cd80ea31f0dcfaa9dffb1cd446d9a99b&q=uray
Processing Record 234| Airai
http://api.openweathermap.org/data/2.5/weather?appid=cd80ea31f0dcfaa9dffb1cd446d9a99b&q=airai
city not found ... skipping 
Processing Record 235| Iberia
http://api.openweathermap.org/data/2.5/weather?appid=cd80ea31f0dcfaa9dffb1cd446d9a99b&q=iberia
Processing Record 236| San Cristobal
http://api.openweathermap.org/data/2.5/weather?appid=cd80ea31f0dcfaa9dffb1cd446d9a99b&q=san%20cristobal
Processing Record 237| Warrnambool
http://api.openweathermap.org/data/2.5/weather?appid=cd80ea31f0dcfaa9dffb1cd446d9a99b&q=warrnambool
Processing Record 238| Alice Springs
http://api.openweathermap.org/data/2.5/weather?appid=cd80ea31f0dcfaa9dffb1cd446d9a99b&q=alice%20springs
Processing Record 239| Mega
http://api.openweathermap.org/data/2.5/weather?appid=cd80ea31f0dcfaa9dffb1cd446d9a99b&q=mega
Processing Record 240| Sola
http://api.openweathermap.org/data/2.5/weather?appid=cd80ea31f0dcfaa9dffb1cd446d9a99b&q=sola
Processing Record 241| Dingle
http://api.openweathermap.org/data/2.5/weather?appid=cd80ea31f0dcfaa9dffb1cd446d9a99b&q=dingle
Processing Record 242| Bud
http://api.openweathermap.org/data/2.5/weather?appid=cd80ea31f0dcfaa9dffb1cd446d9a99b&q=bud
Processing Record 243| Pompeia
http://api.openweathermap.org/data/2.5/weather?appid=cd80ea31f0dcfaa9dffb1cd446d9a99b&q=pompeia
Processing Record 244| Miraflores
http://api.openweathermap.org/data/2.5/weather?appid=cd80ea31f0dcfaa9dffb1cd446d9a99b&q=miraflores
Processing Record 245| Rumonge
http://api.openweathermap.org/data/2.5/weather?appid=cd80ea31f0dcfaa9dffb1cd446d9a99b&q=rumonge
Processing Record 246| Salvador
http://api.openweathermap.org/data/2.5/weather?appid=cd80ea31f0dcfaa9dffb1cd446d9a99b&q=salvador
Processing Record 247| Ullapool
http://api.openweathermap.org/data/2.5/weather?appid=cd80ea31f0dcfaa9dffb1cd446d9a99b&q=ullapool
Processing Record 248| Antofagasta
http://api.openweathermap.org/data/2.5/weather?appid=cd80ea31f0dcfaa9dffb1cd446d9a99b&q=antofagasta
Processing Record 249| Pemba
http://api.openweathermap.org/data/2.5/weather?appid=cd80ea31f0dcfaa9dffb1cd446d9a99b&q=pemba
Processing Record 250| Ponta do Sol
http://api.openweathermap.org/data/2.5/weather?appid=cd80ea31f0dcfaa9dffb1cd446d9a99b&q=ponta%20do%20sol
Processing Record 251| Synya
http://api.openweathermap.org/data/2.5/weather?appid=cd80ea31f0dcfaa9dffb1cd446d9a99b&q=synya
Processing Record 252| Norman Wells
http://api.openweathermap.org/data/2.5/weather?appid=cd80ea31f0dcfaa9dffb1cd446d9a99b&q=norman%20wells
Processing Record 253| Port Hardy
http://api.openweathermap.org/data/2.5/weather?appid=cd80ea31f0dcfaa9dffb1cd446d9a99b&q=port%20hardy
Processing Record 254| Cayenne
http://api.openweathermap.org/data/2.5/weather?appid=cd80ea31f0dcfaa9dffb1cd446d9a99b&q=cayenne
Processing Record 255| Kavieng
http://api.openweathermap.org/data/2.5/weather?appid=cd80ea31f0dcfaa9dffb1cd446d9a99b&q=kavieng
Processing Record 256| Sistranda
http://api.openweathermap.org/data/2.5/weather?appid=cd80ea31f0dcfaa9dffb1cd446d9a99b&q=sistranda
Processing Record 257| Potenza
http://api.openweathermap.org/data/2.5/weather?appid=cd80ea31f0dcfaa9dffb1cd446d9a99b&q=potenza
Processing Record 258| Dubbo
http://api.openweathermap.org/data/2.5/weather?appid=cd80ea31f0dcfaa9dffb1cd446d9a99b&q=dubbo
Processing Record 259| Prince Rupert
http://api.openweathermap.org/data/2.5/weather?appid=cd80ea31f0dcfaa9dffb1cd446d9a99b&q=prince%20rupert
Processing Record 260| Na Wa
http://api.openweathermap.org/data/2.5/weather?appid=cd80ea31f0dcfaa9dffb1cd446d9a99b&q=na%20wa
Processing Record 261| Auki
http://api.openweathermap.org/data/2.5/weather?appid=cd80ea31f0dcfaa9dffb1cd446d9a99b&q=auki
Processing Record 262| Broken Hill
http://api.openweathermap.org/data/2.5/weather?appid=cd80ea31f0dcfaa9dffb1cd446d9a99b&q=broken%20hill
Processing Record 263| Pangnirtung
http://api.openweathermap.org/data/2.5/weather?appid=cd80ea31f0dcfaa9dffb1cd446d9a99b&q=pangnirtung
Processing Record 264| Pochutla
http://api.openweathermap.org/data/2.5/weather?appid=cd80ea31f0dcfaa9dffb1cd446d9a99b&q=pochutla
Processing Record 265| Harper
http://api.openweathermap.org/data/2.5/weather?appid=cd80ea31f0dcfaa9dffb1cd446d9a99b&q=harper
Processing Record 266| Moerai
http://api.openweathermap.org/data/2.5/weather?appid=cd80ea31f0dcfaa9dffb1cd446d9a99b&q=moerai
Processing Record 267| Naranjal
http://api.openweathermap.org/data/2.5/weather?appid=cd80ea31f0dcfaa9dffb1cd446d9a99b&q=naranjal
Processing Record 268| Kilindoni
http://api.openweathermap.org/data/2.5/weather?appid=cd80ea31f0dcfaa9dffb1cd446d9a99b&q=kilindoni
Processing Record 269| Vilhena
http://api.openweathermap.org/data/2.5/weather?appid=cd80ea31f0dcfaa9dffb1cd446d9a99b&q=vilhena
Processing Record 270| Chokurdakh
http://api.openweathermap.org/data/2.5/weather?appid=cd80ea31f0dcfaa9dffb1cd446d9a99b&q=chokurdakh
Processing Record 271| Mecca
http://api.openweathermap.org/data/2.5/weather?appid=cd80ea31f0dcfaa9dffb1cd446d9a99b&q=mecca
Processing Record 272| Peshkovo
http://api.openweathermap.org/data/2.5/weather?appid=cd80ea31f0dcfaa9dffb1cd446d9a99b&q=peshkovo
Processing Record 273| Saskylakh
http://api.openweathermap.org/data/2.5/weather?appid=cd80ea31f0dcfaa9dffb1cd446d9a99b&q=saskylakh
Processing Record 274| Waddan
http://api.openweathermap.org/data/2.5/weather?appid=cd80ea31f0dcfaa9dffb1cd446d9a99b&q=waddan
Processing Record 275| Sorland
http://api.openweathermap.org/data/2.5/weather?appid=cd80ea31f0dcfaa9dffb1cd446d9a99b&q=sorland
Processing Record 276| Ancud
http://api.openweathermap.org/data/2.5/weather?appid=cd80ea31f0dcfaa9dffb1cd446d9a99b&q=ancud
Processing Record 277| Port Lincoln
http://api.openweathermap.org/data/2.5/weather?appid=cd80ea31f0dcfaa9dffb1cd446d9a99b&q=port%20lincoln
Processing Record 278| Colonia
http://api.openweathermap.org/data/2.5/weather?appid=cd80ea31f0dcfaa9dffb1cd446d9a99b&q=colonia
Processing Record 279| Aykhal
http://api.openweathermap.org/data/2.5/weather?appid=cd80ea31f0dcfaa9dffb1cd446d9a99b&q=aykhal
Processing Record 280| Gull Lake
http://api.openweathermap.org/data/2.5/weather?appid=cd80ea31f0dcfaa9dffb1cd446d9a99b&q=gull%20lake
Processing Record 281| Aksarka
http://api.openweathermap.org/data/2.5/weather?appid=cd80ea31f0dcfaa9dffb1cd446d9a99b&q=aksarka
Processing Record 282| Egvekinot
http://api.openweathermap.org/data/2.5/weather?appid=cd80ea31f0dcfaa9dffb1cd446d9a99b&q=egvekinot
Processing Record 283| College
http://api.openweathermap.org/data/2.5/weather?appid=cd80ea31f0dcfaa9dffb1cd446d9a99b&q=college
Processing Record 284| Bethel
http://api.openweathermap.org/data/2.5/weather?appid=cd80ea31f0dcfaa9dffb1cd446d9a99b&q=bethel
Processing Record 285| Lusaka
http://api.openweathermap.org/data/2.5/weather?appid=cd80ea31f0dcfaa9dffb1cd446d9a99b&q=lusaka
Processing Record 286| Ngunguru
http://api.openweathermap.org/data/2.5/weather?appid=cd80ea31f0dcfaa9dffb1cd446d9a99b&q=ngunguru
Processing Record 287| Luganville
http://api.openweathermap.org/data/2.5/weather?appid=cd80ea31f0dcfaa9dffb1cd446d9a99b&q=luganville
city not found ... skipping 
Processing Record 288| Eucaliptus
http://api.openweathermap.org/data/2.5/weather?appid=cd80ea31f0dcfaa9dffb1cd446d9a99b&q=eucaliptus
city not found ... skipping 
Processing Record 289| Nioro
http://api.openweathermap.org/data/2.5/weather?appid=cd80ea31f0dcfaa9dffb1cd446d9a99b&q=nioro
Processing Record 290| Huarmey
http://api.openweathermap.org/data/2.5/weather?appid=cd80ea31f0dcfaa9dffb1cd446d9a99b&q=huarmey
Processing Record 291| Bathsheba
http://api.openweathermap.org/data/2.5/weather?appid=cd80ea31f0dcfaa9dffb1cd446d9a99b&q=bathsheba
city not found ... skipping 
Processing Record 292| Korem
http://api.openweathermap.org/data/2.5/weather?appid=cd80ea31f0dcfaa9dffb1cd446d9a99b&q=korem
Processing Record 293| Timmins
http://api.openweathermap.org/data/2.5/weather?appid=cd80ea31f0dcfaa9dffb1cd446d9a99b&q=timmins
Processing Record 294| Selma
http://api.openweathermap.org/data/2.5/weather?appid=cd80ea31f0dcfaa9dffb1cd446d9a99b&q=selma
Processing Record 295| Murakami
http://api.openweathermap.org/data/2.5/weather?appid=cd80ea31f0dcfaa9dffb1cd446d9a99b&q=murakami
Processing Record 296| Maragogi
http://api.openweathermap.org/data/2.5/weather?appid=cd80ea31f0dcfaa9dffb1cd446d9a99b&q=maragogi
Processing Record 297| Beringovskiy
http://api.openweathermap.org/data/2.5/weather?appid=cd80ea31f0dcfaa9dffb1cd446d9a99b&q=beringovskiy
city not found ... skipping 
Processing Record 298| Saint-Joseph
http://api.openweathermap.org/data/2.5/weather?appid=cd80ea31f0dcfaa9dffb1cd446d9a99b&q=saint-joseph
Processing Record 299| Bara
http://api.openweathermap.org/data/2.5/weather?appid=cd80ea31f0dcfaa9dffb1cd446d9a99b&q=bara
Processing Record 300| Erzin
http://api.openweathermap.org/data/2.5/weather?appid=cd80ea31f0dcfaa9dffb1cd446d9a99b&q=erzin
Processing Record 301| Zaraysk
http://api.openweathermap.org/data/2.5/weather?appid=cd80ea31f0dcfaa9dffb1cd446d9a99b&q=zaraysk
Processing Record 302| Sao Jose da Coroa Grande
http://api.openweathermap.org/data/2.5/weather?appid=cd80ea31f0dcfaa9dffb1cd446d9a99b&q=sao%20jose%20da%20coroa%20grande
Processing Record 303| Rocha
http://api.openweathermap.org/data/2.5/weather?appid=cd80ea31f0dcfaa9dffb1cd446d9a99b&q=rocha
Processing Record 304| Batagay-Alyta
http://api.openweathermap.org/data/2.5/weather?appid=cd80ea31f0dcfaa9dffb1cd446d9a99b&q=batagay-alyta
Processing Record 305| Yulara
http://api.openweathermap.org/data/2.5/weather?appid=cd80ea31f0dcfaa9dffb1cd446d9a99b&q=yulara
Processing Record 306| Mareeba
http://api.openweathermap.org/data/2.5/weather?appid=cd80ea31f0dcfaa9dffb1cd446d9a99b&q=mareeba
Processing Record 307| Chiredzi
http://api.openweathermap.org/data/2.5/weather?appid=cd80ea31f0dcfaa9dffb1cd446d9a99b&q=chiredzi
Processing Record 308| Karla
http://api.openweathermap.org/data/2.5/weather?appid=cd80ea31f0dcfaa9dffb1cd446d9a99b&q=karla
Processing Record 309| Labuhan
http://api.openweathermap.org/data/2.5/weather?appid=cd80ea31f0dcfaa9dffb1cd446d9a99b&q=labuhan
Processing Record 310| Quelimane
http://api.openweathermap.org/data/2.5/weather?appid=cd80ea31f0dcfaa9dffb1cd446d9a99b&q=quelimane
Processing Record 311| Krasnyy Yar
http://api.openweathermap.org/data/2.5/weather?appid=cd80ea31f0dcfaa9dffb1cd446d9a99b&q=krasnyy%20yar
city not found ... skipping 
Processing Record 312| Chambishi
http://api.openweathermap.org/data/2.5/weather?appid=cd80ea31f0dcfaa9dffb1cd446d9a99b&q=chambishi
Processing Record 313| Pitimbu
http://api.openweathermap.org/data/2.5/weather?appid=cd80ea31f0dcfaa9dffb1cd446d9a99b&q=pitimbu
Processing Record 314| Erenhot
http://api.openweathermap.org/data/2.5/weather?appid=cd80ea31f0dcfaa9dffb1cd446d9a99b&q=erenhot
Processing Record 315| Morondava
http://api.openweathermap.org/data/2.5/weather?appid=cd80ea31f0dcfaa9dffb1cd446d9a99b&q=morondava
Processing Record 316| Naryan-Mar
http://api.openweathermap.org/data/2.5/weather?appid=cd80ea31f0dcfaa9dffb1cd446d9a99b&q=naryan-mar
Processing Record 317| Hay River
http://api.openweathermap.org/data/2.5/weather?appid=cd80ea31f0dcfaa9dffb1cd446d9a99b&q=hay%20river
Processing Record 318| Ucluelet
http://api.openweathermap.org/data/2.5/weather?appid=cd80ea31f0dcfaa9dffb1cd446d9a99b&q=ucluelet
Processing Record 319| Bandarbeyla
http://api.openweathermap.org/data/2.5/weather?appid=cd80ea31f0dcfaa9dffb1cd446d9a99b&q=bandarbeyla
Processing Record 320| Ponta Delgada
http://api.openweathermap.org/data/2.5/weather?appid=cd80ea31f0dcfaa9dffb1cd446d9a99b&q=ponta%20delgada
Processing Record 321| Hit
http://api.openweathermap.org/data/2.5/weather?appid=cd80ea31f0dcfaa9dffb1cd446d9a99b&q=hit
city not found ... skipping 
Processing Record 322| Freeport
http://api.openweathermap.org/data/2.5/weather?appid=cd80ea31f0dcfaa9dffb1cd446d9a99b&q=freeport
Processing Record 323| Strezhevoy
http://api.openweathermap.org/data/2.5/weather?appid=cd80ea31f0dcfaa9dffb1cd446d9a99b&q=strezhevoy
Processing Record 324| Waitati
http://api.openweathermap.org/data/2.5/weather?appid=cd80ea31f0dcfaa9dffb1cd446d9a99b&q=waitati
Processing Record 325| Aklavik
http://api.openweathermap.org/data/2.5/weather?appid=cd80ea31f0dcfaa9dffb1cd446d9a99b&q=aklavik
Processing Record 326| Izmalkovo
http://api.openweathermap.org/data/2.5/weather?appid=cd80ea31f0dcfaa9dffb1cd446d9a99b&q=izmalkovo
Processing Record 327| Lata
http://api.openweathermap.org/data/2.5/weather?appid=cd80ea31f0dcfaa9dffb1cd446d9a99b&q=lata
Processing Record 328| Opuwo
http://api.openweathermap.org/data/2.5/weather?appid=cd80ea31f0dcfaa9dffb1cd446d9a99b&q=opuwo
Processing Record 329| Sinnamary
http://api.openweathermap.org/data/2.5/weather?appid=cd80ea31f0dcfaa9dffb1cd446d9a99b&q=sinnamary
Processing Record 330| Lebu
http://api.openweathermap.org/data/2.5/weather?appid=cd80ea31f0dcfaa9dffb1cd446d9a99b&q=lebu
Processing Record 331| Saint-Georges
http://api.openweathermap.org/data/2.5/weather?appid=cd80ea31f0dcfaa9dffb1cd446d9a99b&q=saint-georges
Processing Record 332| Kankan
http://api.openweathermap.org/data/2.5/weather?appid=cd80ea31f0dcfaa9dffb1cd446d9a99b&q=kankan
Processing Record 333| Bowen
http://api.openweathermap.org/data/2.5/weather?appid=cd80ea31f0dcfaa9dffb1cd446d9a99b&q=bowen
Processing Record 334| Praia da Vitoria
http://api.openweathermap.org/data/2.5/weather?appid=cd80ea31f0dcfaa9dffb1cd446d9a99b&q=praia%20da%20vitoria
city not found ... skipping 
Processing Record 335| Ballina
http://api.openweathermap.org/data/2.5/weather?appid=cd80ea31f0dcfaa9dffb1cd446d9a99b&q=ballina
Processing Record 336| Manama
http://api.openweathermap.org/data/2.5/weather?appid=cd80ea31f0dcfaa9dffb1cd446d9a99b&q=manama
Processing Record 337| Ewa Beach
http://api.openweathermap.org/data/2.5/weather?appid=cd80ea31f0dcfaa9dffb1cd446d9a99b&q=ewa%20beach
Processing Record 338| Laguna
http://api.openweathermap.org/data/2.5/weather?appid=cd80ea31f0dcfaa9dffb1cd446d9a99b&q=laguna
Processing Record 339| Piacabucu
http://api.openweathermap.org/data/2.5/weather?appid=cd80ea31f0dcfaa9dffb1cd446d9a99b&q=piacabucu
Processing Record 340| Upernavik
http://api.openweathermap.org/data/2.5/weather?appid=cd80ea31f0dcfaa9dffb1cd446d9a99b&q=upernavik
Processing Record 341| Faya
http://api.openweathermap.org/data/2.5/weather?appid=cd80ea31f0dcfaa9dffb1cd446d9a99b&q=faya
Processing Record 342| Vila Franca do Campo
http://api.openweathermap.org/data/2.5/weather?appid=cd80ea31f0dcfaa9dffb1cd446d9a99b&q=vila%20franca%20do%20campo
Processing Record 343| Pokaran
http://api.openweathermap.org/data/2.5/weather?appid=cd80ea31f0dcfaa9dffb1cd446d9a99b&q=pokaran
Processing Record 344| Vao
http://api.openweathermap.org/data/2.5/weather?appid=cd80ea31f0dcfaa9dffb1cd446d9a99b&q=vao
city not found ... skipping 
Processing Record 345| Kahului
http://api.openweathermap.org/data/2.5/weather?appid=cd80ea31f0dcfaa9dffb1cd446d9a99b&q=kahului
Processing Record 346| Jacareacanga
http://api.openweathermap.org/data/2.5/weather?appid=cd80ea31f0dcfaa9dffb1cd446d9a99b&q=jacareacanga
Processing Record 347| Zeya
http://api.openweathermap.org/data/2.5/weather?appid=cd80ea31f0dcfaa9dffb1cd446d9a99b&q=zeya
Processing Record 348| Biloela
http://api.openweathermap.org/data/2.5/weather?appid=cd80ea31f0dcfaa9dffb1cd446d9a99b&q=biloela
Processing Record 349| Simao
http://api.openweathermap.org/data/2.5/weather?appid=cd80ea31f0dcfaa9dffb1cd446d9a99b&q=simao
Processing Record 350| Medea
http://api.openweathermap.org/data/2.5/weather?appid=cd80ea31f0dcfaa9dffb1cd446d9a99b&q=medea
Processing Record 351| Kupang
http://api.openweathermap.org/data/2.5/weather?appid=cd80ea31f0dcfaa9dffb1cd446d9a99b&q=kupang
Processing Record 352| Candolim
http://api.openweathermap.org/data/2.5/weather?appid=cd80ea31f0dcfaa9dffb1cd446d9a99b&q=candolim
Processing Record 353| Marawi
http://api.openweathermap.org/data/2.5/weather?appid=cd80ea31f0dcfaa9dffb1cd446d9a99b&q=marawi
Processing Record 354| Rawson
http://api.openweathermap.org/data/2.5/weather?appid=cd80ea31f0dcfaa9dffb1cd446d9a99b&q=rawson
Processing Record 355| Nisia Floresta
http://api.openweathermap.org/data/2.5/weather?appid=cd80ea31f0dcfaa9dffb1cd446d9a99b&q=nisia%20floresta
Processing Record 356| Galle
http://api.openweathermap.org/data/2.5/weather?appid=cd80ea31f0dcfaa9dffb1cd446d9a99b&q=galle
Processing Record 357| Itabira
http://api.openweathermap.org/data/2.5/weather?appid=cd80ea31f0dcfaa9dffb1cd446d9a99b&q=itabira
Processing Record 358| Husavik
http://api.openweathermap.org/data/2.5/weather?appid=cd80ea31f0dcfaa9dffb1cd446d9a99b&q=husavik
Processing Record 359| Guatire
http://api.openweathermap.org/data/2.5/weather?appid=cd80ea31f0dcfaa9dffb1cd446d9a99b&q=guatire
Processing Record 360| Rajpur
http://api.openweathermap.org/data/2.5/weather?appid=cd80ea31f0dcfaa9dffb1cd446d9a99b&q=rajpur
Processing Record 361| Gao
http://api.openweathermap.org/data/2.5/weather?appid=cd80ea31f0dcfaa9dffb1cd446d9a99b&q=gao
Processing Record 362| Ulladulla
http://api.openweathermap.org/data/2.5/weather?appid=cd80ea31f0dcfaa9dffb1cd446d9a99b&q=ulladulla
Processing Record 363| Willmar
http://api.openweathermap.org/data/2.5/weather?appid=cd80ea31f0dcfaa9dffb1cd446d9a99b&q=willmar
Processing Record 364| Tuatapere
http://api.openweathermap.org/data/2.5/weather?appid=cd80ea31f0dcfaa9dffb1cd446d9a99b&q=tuatapere
Processing Record 365| Eldorado
http://api.openweathermap.org/data/2.5/weather?appid=cd80ea31f0dcfaa9dffb1cd446d9a99b&q=eldorado
Processing Record 366| Brownsville
http://api.openweathermap.org/data/2.5/weather?appid=cd80ea31f0dcfaa9dffb1cd446d9a99b&q=brownsville
Processing Record 367| Waingapu
http://api.openweathermap.org/data/2.5/weather?appid=cd80ea31f0dcfaa9dffb1cd446d9a99b&q=waingapu
Processing Record 368| Arusha
http://api.openweathermap.org/data/2.5/weather?appid=cd80ea31f0dcfaa9dffb1cd446d9a99b&q=arusha
Processing Record 369| Fare
http://api.openweathermap.org/data/2.5/weather?appid=cd80ea31f0dcfaa9dffb1cd446d9a99b&q=fare
Processing Record 370| Maputo
http://api.openweathermap.org/data/2.5/weather?appid=cd80ea31f0dcfaa9dffb1cd446d9a99b&q=maputo
Processing Record 371| Dakar
http://api.openweathermap.org/data/2.5/weather?appid=cd80ea31f0dcfaa9dffb1cd446d9a99b&q=dakar
city not found ... skipping 
Processing Record 372| Shimoda
http://api.openweathermap.org/data/2.5/weather?appid=cd80ea31f0dcfaa9dffb1cd446d9a99b&q=shimoda
Processing Record 373| Ambalavao
http://api.openweathermap.org/data/2.5/weather?appid=cd80ea31f0dcfaa9dffb1cd446d9a99b&q=ambalavao
Processing Record 374| Jizan
http://api.openweathermap.org/data/2.5/weather?appid=cd80ea31f0dcfaa9dffb1cd446d9a99b&q=jizan
Processing Record 375| Sergeyevka
http://api.openweathermap.org/data/2.5/weather?appid=cd80ea31f0dcfaa9dffb1cd446d9a99b&q=sergeyevka
Processing Record 376| Gizo
http://api.openweathermap.org/data/2.5/weather?appid=cd80ea31f0dcfaa9dffb1cd446d9a99b&q=gizo
Processing Record 377| Luderitz
http://api.openweathermap.org/data/2.5/weather?appid=cd80ea31f0dcfaa9dffb1cd446d9a99b&q=luderitz
city not found ... skipping 
Processing Record 378| Tinskoy
http://api.openweathermap.org/data/2.5/weather?appid=cd80ea31f0dcfaa9dffb1cd446d9a99b&q=tinskoy
Processing Record 379| Bereda
http://api.openweathermap.org/data/2.5/weather?appid=cd80ea31f0dcfaa9dffb1cd446d9a99b&q=bereda
Processing Record 380| Coahuayana
http://api.openweathermap.org/data/2.5/weather?appid=cd80ea31f0dcfaa9dffb1cd446d9a99b&q=coahuayana
Processing Record 381| Vallam
http://api.openweathermap.org/data/2.5/weather?appid=cd80ea31f0dcfaa9dffb1cd446d9a99b&q=vallam
Processing Record 382| Novouzensk
http://api.openweathermap.org/data/2.5/weather?appid=cd80ea31f0dcfaa9dffb1cd446d9a99b&q=novouzensk
Processing Record 383| Yining
http://api.openweathermap.org/data/2.5/weather?appid=cd80ea31f0dcfaa9dffb1cd446d9a99b&q=yining
Processing Record 384| Guymon
http://api.openweathermap.org/data/2.5/weather?appid=cd80ea31f0dcfaa9dffb1cd446d9a99b&q=guymon
Processing Record 385| Mabaruma
http://api.openweathermap.org/data/2.5/weather?appid=cd80ea31f0dcfaa9dffb1cd446d9a99b&q=mabaruma
Processing Record 386| Lasa
http://api.openweathermap.org/data/2.5/weather?appid=cd80ea31f0dcfaa9dffb1cd446d9a99b&q=lasa
Processing Record 387| Samarai
http://api.openweathermap.org/data/2.5/weather?appid=cd80ea31f0dcfaa9dffb1cd446d9a99b&q=samarai
Processing Record 388| Baracoa
http://api.openweathermap.org/data/2.5/weather?appid=cd80ea31f0dcfaa9dffb1cd446d9a99b&q=baracoa
Processing Record 389| Buchanan
http://api.openweathermap.org/data/2.5/weather?appid=cd80ea31f0dcfaa9dffb1cd446d9a99b&q=buchanan
Processing Record 390| Axim
http://api.openweathermap.org/data/2.5/weather?appid=cd80ea31f0dcfaa9dffb1cd446d9a99b&q=axim
Processing Record 391| Ylivieska
http://api.openweathermap.org/data/2.5/weather?appid=cd80ea31f0dcfaa9dffb1cd446d9a99b&q=ylivieska
Processing Record 392| Deputatskiy
http://api.openweathermap.org/data/2.5/weather?appid=cd80ea31f0dcfaa9dffb1cd446d9a99b&q=deputatskiy
city not found ... skipping 
Processing Record 393| Tabou
http://api.openweathermap.org/data/2.5/weather?appid=cd80ea31f0dcfaa9dffb1cd446d9a99b&q=tabou
Processing Record 394| Carbondale
http://api.openweathermap.org/data/2.5/weather?appid=cd80ea31f0dcfaa9dffb1cd446d9a99b&q=carbondale
Processing Record 395| Aracoiaba da Serra
http://api.openweathermap.org/data/2.5/weather?appid=cd80ea31f0dcfaa9dffb1cd446d9a99b&q=aracoiaba%20da%20serra
Processing Record 396| Banjar
http://api.openweathermap.org/data/2.5/weather?appid=cd80ea31f0dcfaa9dffb1cd446d9a99b&q=banjar
Processing Record 397| Porto Velho
http://api.openweathermap.org/data/2.5/weather?appid=cd80ea31f0dcfaa9dffb1cd446d9a99b&q=porto%20velho
Processing Record 398| Mirabad
http://api.openweathermap.org/data/2.5/weather?appid=cd80ea31f0dcfaa9dffb1cd446d9a99b&q=mirabad
Processing Record 399| San Jose
http://api.openweathermap.org/data/2.5/weather?appid=cd80ea31f0dcfaa9dffb1cd446d9a99b&q=san%20jose
Processing Record 400| Hagenow
http://api.openweathermap.org/data/2.5/weather?appid=cd80ea31f0dcfaa9dffb1cd446d9a99b&q=hagenow
Processing Record 401| Vardo
http://api.openweathermap.org/data/2.5/weather?appid=cd80ea31f0dcfaa9dffb1cd446d9a99b&q=vardo
city not found ... skipping 
Processing Record 402| Zhangye
http://api.openweathermap.org/data/2.5/weather?appid=cd80ea31f0dcfaa9dffb1cd446d9a99b&q=zhangye
Processing Record 403| Padang
http://api.openweathermap.org/data/2.5/weather?appid=cd80ea31f0dcfaa9dffb1cd446d9a99b&q=padang
Processing Record 404| Doda
http://api.openweathermap.org/data/2.5/weather?appid=cd80ea31f0dcfaa9dffb1cd446d9a99b&q=doda
Processing Record 405| Cabedelo
http://api.openweathermap.org/data/2.5/weather?appid=cd80ea31f0dcfaa9dffb1cd446d9a99b&q=cabedelo
Processing Record 406| Clyde River
http://api.openweathermap.org/data/2.5/weather?appid=cd80ea31f0dcfaa9dffb1cd446d9a99b&q=clyde%20river
Processing Record 407| Balakirevo
http://api.openweathermap.org/data/2.5/weather?appid=cd80ea31f0dcfaa9dffb1cd446d9a99b&q=balakirevo
city not found ... skipping 
Processing Record 408| Lardos
http://api.openweathermap.org/data/2.5/weather?appid=cd80ea31f0dcfaa9dffb1cd446d9a99b&q=lardos
Processing Record 409| Namatanai
http://api.openweathermap.org/data/2.5/weather?appid=cd80ea31f0dcfaa9dffb1cd446d9a99b&q=namatanai
Processing Record 410| Warrington
http://api.openweathermap.org/data/2.5/weather?appid=cd80ea31f0dcfaa9dffb1cd446d9a99b&q=warrington
Processing Record 411| Suntar
http://api.openweathermap.org/data/2.5/weather?appid=cd80ea31f0dcfaa9dffb1cd446d9a99b&q=suntar
Processing Record 412| Kaitangata
http://api.openweathermap.org/data/2.5/weather?appid=cd80ea31f0dcfaa9dffb1cd446d9a99b&q=kaitangata
Processing Record 413| Nizhniy Odes
http://api.openweathermap.org/data/2.5/weather?appid=cd80ea31f0dcfaa9dffb1cd446d9a99b&q=nizhniy%20odes
Processing Record 414| Buenos Aires
http://api.openweathermap.org/data/2.5/weather?appid=cd80ea31f0dcfaa9dffb1cd446d9a99b&q=buenos%20aires
Processing Record 415| Aktau
http://api.openweathermap.org/data/2.5/weather?appid=cd80ea31f0dcfaa9dffb1cd446d9a99b&q=aktau
Processing Record 416| Katsuura
http://api.openweathermap.org/data/2.5/weather?appid=cd80ea31f0dcfaa9dffb1cd446d9a99b&q=katsuura
Processing Record 417| Watari
http://api.openweathermap.org/data/2.5/weather?appid=cd80ea31f0dcfaa9dffb1cd446d9a99b&q=watari
Processing Record 418| Laela
http://api.openweathermap.org/data/2.5/weather?appid=cd80ea31f0dcfaa9dffb1cd446d9a99b&q=laela
Processing Record 419| Diapaga
http://api.openweathermap.org/data/2.5/weather?appid=cd80ea31f0dcfaa9dffb1cd446d9a99b&q=diapaga
Processing Record 420| Leh
http://api.openweathermap.org/data/2.5/weather?appid=cd80ea31f0dcfaa9dffb1cd446d9a99b&q=leh
city not found ... skipping 
Processing Record 421| Oltu
http://api.openweathermap.org/data/2.5/weather?appid=cd80ea31f0dcfaa9dffb1cd446d9a99b&q=oltu
Processing Record 422| Roald
http://api.openweathermap.org/data/2.5/weather?appid=cd80ea31f0dcfaa9dffb1cd446d9a99b&q=roald
city not found ... skipping 
Processing Record 423| Te Anau
http://api.openweathermap.org/data/2.5/weather?appid=cd80ea31f0dcfaa9dffb1cd446d9a99b&q=te%20anau
Processing Record 424| Novaya Lyalya
http://api.openweathermap.org/data/2.5/weather?appid=cd80ea31f0dcfaa9dffb1cd446d9a99b&q=novaya%20lyalya
Processing Record 425| Hirtshals
http://api.openweathermap.org/data/2.5/weather?appid=cd80ea31f0dcfaa9dffb1cd446d9a99b&q=hirtshals
Processing Record 426| Farap
http://api.openweathermap.org/data/2.5/weather?appid=cd80ea31f0dcfaa9dffb1cd446d9a99b&q=farap
Processing Record 427| Warri
http://api.openweathermap.org/data/2.5/weather?appid=cd80ea31f0dcfaa9dffb1cd446d9a99b&q=warri
city not found ... skipping 
Processing Record 428| Fukue
http://api.openweathermap.org/data/2.5/weather?appid=cd80ea31f0dcfaa9dffb1cd446d9a99b&q=fukue
Processing Record 429| Vinh
http://api.openweathermap.org/data/2.5/weather?appid=cd80ea31f0dcfaa9dffb1cd446d9a99b&q=vinh
Processing Record 430| Kamenka
http://api.openweathermap.org/data/2.5/weather?appid=cd80ea31f0dcfaa9dffb1cd446d9a99b&q=kamenka
Processing Record 431| Okaihau
http://api.openweathermap.org/data/2.5/weather?appid=cd80ea31f0dcfaa9dffb1cd446d9a99b&q=okaihau
Processing Record 432| Ust-Maya
http://api.openweathermap.org/data/2.5/weather?appid=cd80ea31f0dcfaa9dffb1cd446d9a99b&q=ust-maya
Processing Record 433| Iquitos
http://api.openweathermap.org/data/2.5/weather?appid=cd80ea31f0dcfaa9dffb1cd446d9a99b&q=iquitos
Processing Record 434| Paragominas
http://api.openweathermap.org/data/2.5/weather?appid=cd80ea31f0dcfaa9dffb1cd446d9a99b&q=paragominas
Processing Record 435| Fonte Boa
http://api.openweathermap.org/data/2.5/weather?appid=cd80ea31f0dcfaa9dffb1cd446d9a99b&q=fonte%20boa
Processing Record 436| Yenagoa
http://api.openweathermap.org/data/2.5/weather?appid=cd80ea31f0dcfaa9dffb1cd446d9a99b&q=yenagoa
Processing Record 437| Klaksvik
http://api.openweathermap.org/data/2.5/weather?appid=cd80ea31f0dcfaa9dffb1cd446d9a99b&q=klaksvik
city not found ... skipping 
Processing Record 438| Kruisfontein
http://api.openweathermap.org/data/2.5/weather?appid=cd80ea31f0dcfaa9dffb1cd446d9a99b&q=kruisfontein
Processing Record 439| Sijunjung
http://api.openweathermap.org/data/2.5/weather?appid=cd80ea31f0dcfaa9dffb1cd446d9a99b&q=sijunjung
Processing Record 440| Tessalit
http://api.openweathermap.org/data/2.5/weather?appid=cd80ea31f0dcfaa9dffb1cd446d9a99b&q=tessalit
Processing Record 441| Dunkwa
http://api.openweathermap.org/data/2.5/weather?appid=cd80ea31f0dcfaa9dffb1cd446d9a99b&q=dunkwa
Processing Record 442| Kidal
http://api.openweathermap.org/data/2.5/weather?appid=cd80ea31f0dcfaa9dffb1cd446d9a99b&q=kidal
Processing Record 443| Alpena
http://api.openweathermap.org/data/2.5/weather?appid=cd80ea31f0dcfaa9dffb1cd446d9a99b&q=alpena
Processing Record 444| Mizan Teferi
http://api.openweathermap.org/data/2.5/weather?appid=cd80ea31f0dcfaa9dffb1cd446d9a99b&q=mizan%20teferi
Processing Record 445| Ola
http://api.openweathermap.org/data/2.5/weather?appid=cd80ea31f0dcfaa9dffb1cd446d9a99b&q=ola
Processing Record 446| Matamoros
http://api.openweathermap.org/data/2.5/weather?appid=cd80ea31f0dcfaa9dffb1cd446d9a99b&q=matamoros
Processing Record 447| Tateyama
http://api.openweathermap.org/data/2.5/weather?appid=cd80ea31f0dcfaa9dffb1cd446d9a99b&q=tateyama
Processing Record 448| Petropavlovsk-Kamchatskiy
http://api.openweathermap.org/data/2.5/weather?appid=cd80ea31f0dcfaa9dffb1cd446d9a99b&q=petropavlovsk-kamchatskiy
Processing Record 449| Kiruna
http://api.openweathermap.org/data/2.5/weather?appid=cd80ea31f0dcfaa9dffb1cd446d9a99b&q=kiruna
city not found ... skipping 
Processing Record 450| Dmitriyevka
http://api.openweathermap.org/data/2.5/weather?appid=cd80ea31f0dcfaa9dffb1cd446d9a99b&q=dmitriyevka
Processing Record 451| Wanaka
http://api.openweathermap.org/data/2.5/weather?appid=cd80ea31f0dcfaa9dffb1cd446d9a99b&q=wanaka
city not found ... skipping 
Processing Record 452| Plettenberg Bay
http://api.openweathermap.org/data/2.5/weather?appid=cd80ea31f0dcfaa9dffb1cd446d9a99b&q=plettenberg%20bay
Processing Record 453| Angren
http://api.openweathermap.org/data/2.5/weather?appid=cd80ea31f0dcfaa9dffb1cd446d9a99b&q=angren
Processing Record 454| Thabazimbi
http://api.openweathermap.org/data/2.5/weather?appid=cd80ea31f0dcfaa9dffb1cd446d9a99b&q=thabazimbi
Processing Record 455| Jieshi
http://api.openweathermap.org/data/2.5/weather?appid=cd80ea31f0dcfaa9dffb1cd446d9a99b&q=jieshi
Processing Record 456| Svetlogorsk
http://api.openweathermap.org/data/2.5/weather?appid=cd80ea31f0dcfaa9dffb1cd446d9a99b&q=svetlogorsk
Processing Record 457| Pringsewu
http://api.openweathermap.org/data/2.5/weather?appid=cd80ea31f0dcfaa9dffb1cd446d9a99b&q=pringsewu
Processing Record 458| Kankaanpaa
http://api.openweathermap.org/data/2.5/weather?appid=cd80ea31f0dcfaa9dffb1cd446d9a99b&q=kankaanpaa
Processing Record 459| Zarechnyy
http://api.openweathermap.org/data/2.5/weather?appid=cd80ea31f0dcfaa9dffb1cd446d9a99b&q=zarechnyy
Processing Record 460| Ormara
http://api.openweathermap.org/data/2.5/weather?appid=cd80ea31f0dcfaa9dffb1cd446d9a99b&q=ormara
Processing Record 461| Puerto El Triunfo
http://api.openweathermap.org/data/2.5/weather?appid=cd80ea31f0dcfaa9dffb1cd446d9a99b&q=puerto%20el%20triunfo
Processing Record 462| Hamada
http://api.openweathermap.org/data/2.5/weather?appid=cd80ea31f0dcfaa9dffb1cd446d9a99b&q=hamada
Processing Record 463| Atbasar
http://api.openweathermap.org/data/2.5/weather?appid=cd80ea31f0dcfaa9dffb1cd446d9a99b&q=atbasar
Processing Record 464| Maposeni
http://api.openweathermap.org/data/2.5/weather?appid=cd80ea31f0dcfaa9dffb1cd446d9a99b&q=maposeni
Processing Record 465| Gat
http://api.openweathermap.org/data/2.5/weather?appid=cd80ea31f0dcfaa9dffb1cd446d9a99b&q=gat
Processing Record 466| Eyemouth
http://api.openweathermap.org/data/2.5/weather?appid=cd80ea31f0dcfaa9dffb1cd446d9a99b&q=eyemouth
Processing Record 467| Ca Mau
http://api.openweathermap.org/data/2.5/weather?appid=cd80ea31f0dcfaa9dffb1cd446d9a99b&q=ca%20mau
city not found ... skipping 
Processing Record 468| Badiraguato
http://api.openweathermap.org/data/2.5/weather?appid=cd80ea31f0dcfaa9dffb1cd446d9a99b&q=badiraguato
Processing Record 469| Karaton
http://api.openweathermap.org/data/2.5/weather?appid=cd80ea31f0dcfaa9dffb1cd446d9a99b&q=karaton
Processing Record 470| Sibolga
http://api.openweathermap.org/data/2.5/weather?appid=cd80ea31f0dcfaa9dffb1cd446d9a99b&q=sibolga
Processing Record 471| Vizinga
http://api.openweathermap.org/data/2.5/weather?appid=cd80ea31f0dcfaa9dffb1cd446d9a99b&q=vizinga
Processing Record 472| Bonthe
http://api.openweathermap.org/data/2.5/weather?appid=cd80ea31f0dcfaa9dffb1cd446d9a99b&q=bonthe
Processing Record 473| Seybaplaya
http://api.openweathermap.org/data/2.5/weather?appid=cd80ea31f0dcfaa9dffb1cd446d9a99b&q=seybaplaya
Processing Record 474| Muisne
http://api.openweathermap.org/data/2.5/weather?appid=cd80ea31f0dcfaa9dffb1cd446d9a99b&q=muisne
Processing Record 475| Mahibadhoo
http://api.openweathermap.org/data/2.5/weather?appid=cd80ea31f0dcfaa9dffb1cd446d9a99b&q=mahibadhoo
Processing Record 476| Portland
http://api.openweathermap.org/data/2.5/weather?appid=cd80ea31f0dcfaa9dffb1cd446d9a99b&q=portland
Processing Record 477| Hengyang
http://api.openweathermap.org/data/2.5/weather?appid=cd80ea31f0dcfaa9dffb1cd446d9a99b&q=hengyang
Processing Record 478| Ifanadiana
http://api.openweathermap.org/data/2.5/weather?appid=cd80ea31f0dcfaa9dffb1cd446d9a99b&q=ifanadiana
Processing Record 479| Kalmunai
http://api.openweathermap.org/data/2.5/weather?appid=cd80ea31f0dcfaa9dffb1cd446d9a99b&q=kalmunai
Processing Record 480| Nichinan
http://api.openweathermap.org/data/2.5/weather?appid=cd80ea31f0dcfaa9dffb1cd446d9a99b&q=nichinan
Processing Record 481| Orlik
http://api.openweathermap.org/data/2.5/weather?appid=cd80ea31f0dcfaa9dffb1cd446d9a99b&q=orlik
Processing Record 482| Mehamn
http://api.openweathermap.org/data/2.5/weather?appid=cd80ea31f0dcfaa9dffb1cd446d9a99b&q=mehamn
Processing Record 483| Praia
http://api.openweathermap.org/data/2.5/weather?appid=cd80ea31f0dcfaa9dffb1cd446d9a99b&q=praia
Processing Record 484| Paamiut
http://api.openweathermap.org/data/2.5/weather?appid=cd80ea31f0dcfaa9dffb1cd446d9a99b&q=paamiut
Processing Record 485| Tayu
http://api.openweathermap.org/data/2.5/weather?appid=cd80ea31f0dcfaa9dffb1cd446d9a99b&q=tayu
Processing Record 486| Santa Marinella
http://api.openweathermap.org/data/2.5/weather?appid=cd80ea31f0dcfaa9dffb1cd446d9a99b&q=santa%20marinella
city not found ... skipping 
Processing Record 487| Aljezur
http://api.openweathermap.org/data/2.5/weather?appid=cd80ea31f0dcfaa9dffb1cd446d9a99b&q=aljezur
Processing Record 488| Kautokeino
http://api.openweathermap.org/data/2.5/weather?appid=cd80ea31f0dcfaa9dffb1cd446d9a99b&q=kautokeino
Processing Record 489| Oktyabrskiy
http://api.openweathermap.org/data/2.5/weather?appid=cd80ea31f0dcfaa9dffb1cd446d9a99b&q=oktyabrskiy
Processing Record 490| Licata
http://api.openweathermap.org/data/2.5/weather?appid=cd80ea31f0dcfaa9dffb1cd446d9a99b&q=licata
city not found ... skipping 
Processing Record 491| Nyurba
http://api.openweathermap.org/data/2.5/weather?appid=cd80ea31f0dcfaa9dffb1cd446d9a99b&q=nyurba
Processing Record 492| Harrisonville
http://api.openweathermap.org/data/2.5/weather?appid=cd80ea31f0dcfaa9dffb1cd446d9a99b&q=harrisonville
Processing Record 493| Mocuba
http://api.openweathermap.org/data/2.5/weather?appid=cd80ea31f0dcfaa9dffb1cd446d9a99b&q=mocuba
Processing Record 494| Price
http://api.openweathermap.org/data/2.5/weather?appid=cd80ea31f0dcfaa9dffb1cd446d9a99b&q=price
Processing Record 495| Melfort
http://api.openweathermap.org/data/2.5/weather?appid=cd80ea31f0dcfaa9dffb1cd446d9a99b&q=melfort
Processing Record 496| Ostrovnoy
http://api.openweathermap.org/data/2.5/weather?appid=cd80ea31f0dcfaa9dffb1cd446d9a99b&q=ostrovnoy
Processing Record 497| Nova Olinda do Norte
http://api.openweathermap.org/data/2.5/weather?appid=cd80ea31f0dcfaa9dffb1cd446d9a99b&q=nova%20olinda%20do%20norte
Processing Record 498| Astoria
http://api.openweathermap.org/data/2.5/weather?appid=cd80ea31f0dcfaa9dffb1cd446d9a99b&q=astoria
Processing Record 499| Copiapo
http://api.openweathermap.org/data/2.5/weather?appid=cd80ea31f0dcfaa9dffb1cd446d9a99b&q=copiapo
Processing Record 500| Talcahuano
http://api.openweathermap.org/data/2.5/weather?appid=cd80ea31f0dcfaa9dffb1cd446d9a99b&q=talcahuano
Processing Record 501| Valsad
http://api.openweathermap.org/data/2.5/weather?appid=cd80ea31f0dcfaa9dffb1cd446d9a99b&q=valsad
Processing Record 502| Phalodi
http://api.openweathermap.org/data/2.5/weather?appid=cd80ea31f0dcfaa9dffb1cd446d9a99b&q=phalodi
Processing Record 503| Byron Bay
http://api.openweathermap.org/data/2.5/weather?appid=cd80ea31f0dcfaa9dffb1cd446d9a99b&q=byron%20bay
Processing Record 504| Colac
http://api.openweathermap.org/data/2.5/weather?appid=cd80ea31f0dcfaa9dffb1cd446d9a99b&q=colac
Processing Record 505| Mount Pleasant
http://api.openweathermap.org/data/2.5/weather?appid=cd80ea31f0dcfaa9dffb1cd446d9a99b&q=mount%20pleasant
Processing Record 506| Kralendijk
http://api.openweathermap.org/data/2.5/weather?appid=cd80ea31f0dcfaa9dffb1cd446d9a99b&q=kralendijk
Processing Record 507| Beyneu
http://api.openweathermap.org/data/2.5/weather?appid=cd80ea31f0dcfaa9dffb1cd446d9a99b&q=beyneu
Processing Record 508| Ambulu
http://api.openweathermap.org/data/2.5/weather?appid=cd80ea31f0dcfaa9dffb1cd446d9a99b&q=ambulu
Processing Record 509| Vung Tau
http://api.openweathermap.org/data/2.5/weather?appid=cd80ea31f0dcfaa9dffb1cd446d9a99b&q=vung%20tau
Processing Record 510| Coos Bay
http://api.openweathermap.org/data/2.5/weather?appid=cd80ea31f0dcfaa9dffb1cd446d9a99b&q=coos%20bay
city not found ... skipping 
Processing Record 511| Letterkenny
http://api.openweathermap.org/data/2.5/weather?appid=cd80ea31f0dcfaa9dffb1cd446d9a99b&q=letterkenny
Processing Record 512| Kavaratti
http://api.openweathermap.org/data/2.5/weather?appid=cd80ea31f0dcfaa9dffb1cd446d9a99b&q=kavaratti
Processing Record 513| Fort Nelson
http://api.openweathermap.org/data/2.5/weather?appid=cd80ea31f0dcfaa9dffb1cd446d9a99b&q=fort%20nelson
Processing Record 514| Calvinia
http://api.openweathermap.org/data/2.5/weather?appid=cd80ea31f0dcfaa9dffb1cd446d9a99b&q=calvinia
Processing Record 515| Goldsboro
http://api.openweathermap.org/data/2.5/weather?appid=cd80ea31f0dcfaa9dffb1cd446d9a99b&q=goldsboro
Processing Record 516| Caravelas
http://api.openweathermap.org/data/2.5/weather?appid=cd80ea31f0dcfaa9dffb1cd446d9a99b&q=caravelas
Processing Record 517| Sabzevar
http://api.openweathermap.org/data/2.5/weather?appid=cd80ea31f0dcfaa9dffb1cd446d9a99b&q=sabzevar
Processing Record 518| Araouane
http://api.openweathermap.org/data/2.5/weather?appid=cd80ea31f0dcfaa9dffb1cd446d9a99b&q=araouane
city not found ... skipping 
Processing Record 519| Clermont
http://api.openweathermap.org/data/2.5/weather?appid=cd80ea31f0dcfaa9dffb1cd446d9a99b&q=clermont
Processing Record 520| Valparaiso
http://api.openweathermap.org/data/2.5/weather?appid=cd80ea31f0dcfaa9dffb1cd446d9a99b&q=valparaiso
Processing Record 521| Namibe
http://api.openweathermap.org/data/2.5/weather?appid=cd80ea31f0dcfaa9dffb1cd446d9a99b&q=namibe
city not found ... skipping 
Processing Record 522| Gornopravdinsk
http://api.openweathermap.org/data/2.5/weather?appid=cd80ea31f0dcfaa9dffb1cd446d9a99b&q=gornopravdinsk
Processing Record 523| Berlevag
http://api.openweathermap.org/data/2.5/weather?appid=cd80ea31f0dcfaa9dffb1cd446d9a99b&q=berlevag
Processing Record 524| Douglas
http://api.openweathermap.org/data/2.5/weather?appid=cd80ea31f0dcfaa9dffb1cd446d9a99b&q=douglas
Processing Record 525| Hanzhong
http://api.openweathermap.org/data/2.5/weather?appid=cd80ea31f0dcfaa9dffb1cd446d9a99b&q=hanzhong
Processing Record 526| Keuruu
http://api.openweathermap.org/data/2.5/weather?appid=cd80ea31f0dcfaa9dffb1cd446d9a99b&q=keuruu
city not found ... skipping 
Processing Record 527| Awjilah
http://api.openweathermap.org/data/2.5/weather?appid=cd80ea31f0dcfaa9dffb1cd446d9a99b&q=awjilah
Processing Record 528| Necochea
http://api.openweathermap.org/data/2.5/weather?appid=cd80ea31f0dcfaa9dffb1cd446d9a99b&q=necochea
Processing Record 529| Sobolevo
http://api.openweathermap.org/data/2.5/weather?appid=cd80ea31f0dcfaa9dffb1cd446d9a99b&q=sobolevo
Processing Record 530| Hawera
http://api.openweathermap.org/data/2.5/weather?appid=cd80ea31f0dcfaa9dffb1cd446d9a99b&q=hawera
Processing Record 531| Srednekolymsk
http://api.openweathermap.org/data/2.5/weather?appid=cd80ea31f0dcfaa9dffb1cd446d9a99b&q=srednekolymsk
Processing Record 532| Ketchikan
http://api.openweathermap.org/data/2.5/weather?appid=cd80ea31f0dcfaa9dffb1cd446d9a99b&q=ketchikan
Processing Record 533| Rio Verde de Mato Grosso
http://api.openweathermap.org/data/2.5/weather?appid=cd80ea31f0dcfaa9dffb1cd446d9a99b&q=rio%20verde%20de%20mato%20grosso
Processing Record 534| Verkhoturye
http://api.openweathermap.org/data/2.5/weather?appid=cd80ea31f0dcfaa9dffb1cd446d9a99b&q=verkhoturye
Processing Record 535| Basoko
http://api.openweathermap.org/data/2.5/weather?appid=cd80ea31f0dcfaa9dffb1cd446d9a99b&q=basoko
Processing Record 536| Metkovic
http://api.openweathermap.org/data/2.5/weather?appid=cd80ea31f0dcfaa9dffb1cd446d9a99b&q=metkovic
Processing Record 537| Mount Isa
http://api.openweathermap.org/data/2.5/weather?appid=cd80ea31f0dcfaa9dffb1cd446d9a99b&q=mount%20isa
Processing Record 538| Turukhansk
http://api.openweathermap.org/data/2.5/weather?appid=cd80ea31f0dcfaa9dffb1cd446d9a99b&q=turukhansk
Processing Record 539| Koslan
http://api.openweathermap.org/data/2.5/weather?appid=cd80ea31f0dcfaa9dffb1cd446d9a99b&q=koslan
Processing Record 540| Tual
http://api.openweathermap.org/data/2.5/weather?appid=cd80ea31f0dcfaa9dffb1cd446d9a99b&q=tual
city not found ... skipping 
Processing Record 541| Oranjestad
http://api.openweathermap.org/data/2.5/weather?appid=cd80ea31f0dcfaa9dffb1cd446d9a99b&q=oranjestad
Processing Record 542| Charlottesville
http://api.openweathermap.org/data/2.5/weather?appid=cd80ea31f0dcfaa9dffb1cd446d9a99b&q=charlottesville
Processing Record 543| Moindou
http://api.openweathermap.org/data/2.5/weather?appid=cd80ea31f0dcfaa9dffb1cd446d9a99b&q=moindou
Processing Record 544| Ikon-Khalk
http://api.openweathermap.org/data/2.5/weather?appid=cd80ea31f0dcfaa9dffb1cd446d9a99b&q=ikon-khalk
city not found ... skipping 
Processing Record 545| Wismar
http://api.openweathermap.org/data/2.5/weather?appid=cd80ea31f0dcfaa9dffb1cd446d9a99b&q=wismar
Processing Record 546| Komsomolskiy
http://api.openweathermap.org/data/2.5/weather?appid=cd80ea31f0dcfaa9dffb1cd446d9a99b&q=komsomolskiy
Processing Record 547| Goderich
http://api.openweathermap.org/data/2.5/weather?appid=cd80ea31f0dcfaa9dffb1cd446d9a99b&q=goderich
Processing Record 548| Santa Cecilia
http://api.openweathermap.org/data/2.5/weather?appid=cd80ea31f0dcfaa9dffb1cd446d9a99b&q=santa%20cecilia
Processing Record 549| Chermoz
http://api.openweathermap.org/data/2.5/weather?appid=cd80ea31f0dcfaa9dffb1cd446d9a99b&q=chermoz
Processing Record 550| Segovia
http://api.openweathermap.org/data/2.5/weather?appid=cd80ea31f0dcfaa9dffb1cd446d9a99b&q=segovia
Processing Record 551| Makushino
http://api.openweathermap.org/data/2.5/weather?appid=cd80ea31f0dcfaa9dffb1cd446d9a99b&q=makushino
Processing Record 552| Derzhavinsk
http://api.openweathermap.org/data/2.5/weather?appid=cd80ea31f0dcfaa9dffb1cd446d9a99b&q=derzhavinsk
Processing Record 553| Mogadishu
http://api.openweathermap.org/data/2.5/weather?appid=cd80ea31f0dcfaa9dffb1cd446d9a99b&q=mogadishu
---Data Retrieval Complete ---



#Convert Raw Data to DataFrame
#Export the city data into a .csv.

#Display the DataFrame

weatherpy_dict = {
    "City": city_name,
    "Cloudiness":cloudiness, 
    "Country":country,
    "Date":date, 
    "Humidity": humidity,
    "Lat":lat, 
    "Lng":lng, 
    "Max Temp": max_temp,
    "Wind Speed":wind_speed
}

# Create a data frame from dictionary
weather_data = pd.DataFrame(weatherpy_dict)

# Display count of weather data values 
weather_data.count()
City          553
Cloudiness    553
Country       553
Date          553
Humidity      553
Lat           553
Lng           553
Max Temp      553
Wind Speed    553
dtype: int64
weather_data
City	Cloudiness	Country	Date	Humidity	Lat	Lng	Max Temp	Wind Speed
0	Yichun	36	CN	1563810305	89	27.80	114.38	299.481	1.22
1	Busselton	100	AU	1563810306	66	-33.64	115.35	285.930	7.34
2	Khatanga	69	RU	1563810308	44	71.98	102.47	295.281	3.06
3	Hermanus	42	ZA	1563810309	68	-34.42	19.24	290.370	7.15
4	Ushuaia	75	AR	1563810275	69	-54.81	-68.31	276.150	2.10
5	Punta Arenas	75	CL	1563810311	80	-53.16	-70.91	277.150	5.70
6	Mataura	33	NZ	1563810312	94	-46.19	168.86	280.370	0.89
7	Montepuez	4	MZ	1563810314	39	-13.13	39.00	295.481	3.21
8	Souillac	0	FR	1563810315	36	45.60	-0.60	308.710	1.50
9	Arraial do Cabo	20	BR	1563810316	57	-22.97	-42.02	299.150	6.20
10	Tiksi	11	RU	1563810317	64	71.64	128.87	279.481	6.06
11	Ryotsu	75	JP	1563810319	94	38.08	138.43	296.150	2.90
12	Uvira	72	CD	1563810320	63	-3.41	29.14	288.181	0.95
13	Mpika	31	ZM	1563810321	49	-11.84	31.40	291.381	4.17
14	Menongue	3	AO	1563810322	8	-14.66	17.68	301.681	3.00
15	Muroto	100	JP	1563810323	94	33.37	134.14	295.981	1.38
16	Sabha	0	LY	1563810325	12	27.03	14.43	309.281	3.85
17	Taltal	21	CL	1563810326	73	-25.41	-70.49	286.581	3.16
18	Daru	100	PG	1563810327	93	-9.07	143.21	296.481	3.69
19	Ploemeur	0	FR	1563810328	57	47.73	-3.43	301.480	3.60
20	Port Elizabeth	1	US	1563810330	58	39.31	-74.98	307.040	3.60
21	Albany	90	US	1563810331	73	42.65	-73.75	295.370	2.10
22	Cidreira	62	BR	1563810332	52	-30.17	-50.22	298.481	3.37
23	Nikolskoye	0	RU	1563810333	29	59.70	30.79	298.150	3.00
24	Hobart	75	AU	1563810203	50	-42.88	147.33	285.150	11.80
25	Huilong	100	CN	1563810336	90	31.15	106.50	299.081	1.28
26	San Policarpo	100	PH	1563810337	87	12.18	125.51	298.881	2.32
27	Vestmannaeyjar	75	IS	1563810338	93	63.44	-20.27	285.150	3.10
28	Lompoc	90	US	1563810340	93	34.64	-120.46	289.820	1.50
29	Hithadhoo	1	MV	1563810341	76	-0.60	73.08	301.681	4.81
...	...	...	...	...	...	...	...	...	...
523	Douglas	75	US	1563810946	93	58.28	-134.39	285.930	1.13
524	Hanzhong	100	CN	1563810948	80	33.08	107.03	295.881	0.60
525	Keuruu	0	FI	1563810949	36	62.26	24.71	300.930	3.10
526	Awjilah	0	LY	1563810950	13	29.14	21.30	309.981	6.77
527	Necochea	80	AR	1563810951	71	-38.55	-58.74	284.820	1.79
528	Sobolevo	100	RU	1563810953	96	54.43	31.90	290.481	1.34
529	Hawera	0	NZ	1563810954	92	-39.59	174.28	280.281	1.42
530	Srednekolymsk	100	RU	1563810955	91	67.46	153.71	277.181	4.84
531	Ketchikan	1	US	1563810956	87	55.34	-131.65	288.150	2.10
532	Rio Verde de Mato Grosso	100	BR	1563810685	34	-18.92	-54.84	302.981	6.34
533	Verkhoturye	100	RU	1563810958	86	58.86	60.81	291.081	0.75
534	Basoko	100	CD	1563810960	54	1.23	23.61	303.081	0.56
535	Metkovic	20	HR	1563810961	43	43.05	17.65	304.150	4.10
536	Mount Isa	0	AU	1563810962	39	-20.73	139.49	283.150	4.51
537	Turukhansk	0	RU	1563810963	50	65.80	87.96	292.881	2.26
538	Koslan	100	RU	1563810965	93	63.46	48.90	287.981	2.89
539	Tual	74	ID	1563810966	80	-5.67	132.75	297.681	8.95
540	Oranjestad	40	AW	1563810825	66	12.52	-70.03	303.150	10.30
541	Charlottesville	1	US	1563810873	59	38.03	-78.48	308.150	4.10
542	Moindou	0	NC	1563810969	87	-21.69	165.68	287.150	1.50
543	Ikon-Khalk	96	RU	1563810971	64	44.32	41.92	294.260	1.79
544	Wismar	75	DE	1563810972	82	53.89	11.46	292.590	2.10
545	Komsomolskiy	99	RU	1563810973	62	67.55	63.78	289.081	6.19
546	Goderich	96	CA	1563810974	75	43.74	-81.71	294.820	3.58
547	Santa Cecilia	75	CR	1563810976	69	9.85	-84.31	298.150	4.10
548	Chermoz	16	RU	1563810977	71	58.79	56.15	291.681	0.86
549	Segovia	0	ES	1563810978	15	40.95	-4.12	311.150	4.10
550	Makushino	95	RU	1563810979	84	55.21	67.25	291.581	3.01
551	Derzhavinsk	64	KZ	1563810980	43	51.10	66.31	297.781	3.88
552	Mogadishu	17	SO	1563810981	71	2.04	45.34	297.981	9.35
553 rows × 9 columns

Plotting the Data
Use proper labeling of the plots using plot titles (including date of analysis) and axes labels.
Save the plotted figures as .pngs.
Latitude vs. Temperature Plot
plt.scatter(weather_data["Lat"], weather_data["Max Temp"], marker="o")

# Incorporate the other graph properties
plt.title("Pressure in World Cities")
plt.ylabel("Pressure (Celsius)")
plt.xlabel("Longitude")
plt.grid(True)

# Save the figure
plt.savefig("PressureInWorldCities.png")

# Show plot
plt.show()

Latitude vs. Humidity Plot
# Build a scatter plot for each data type
plt.scatter(weather_data["Lat"], weather_data["Humidity"], marker="o", s=10)

# Incorporate the other graph properties
plt.title("City Latitude vs. Humidity")
plt.ylabel("Humidity (%)")
plt.xlabel("Latitude")
plt.grid(True)


# Show plot
plt.show()

Latitude vs. Cloudiness Plot
# Build a scatter plot for each data type
plt.scatter(weather_data["Lat"], weather_data["Cloudiness"], marker="o", s=10)

# Incorporate the other graph properties
plt.title("City Latitude vs. Cloudiness")
plt.ylabel("Cloudiness (%)")
plt.xlabel("Latitude")
plt.grid(True)


# Show plot
plt.show()

Latitude vs. Wind Speed Plot
# Build a scatter plot for each data type
plt.scatter(weather_data["Lat"], weather_data["Wind Speed"], marker="o", s=10)

# Incorporate the other graph properties
plt.title("City Latitude vs. Wind Speed")
plt.ylabel("Wind Speed (mph)")
plt.xlabel("Latitude")
plt.grid(True)


# Show plot
plt.show()

