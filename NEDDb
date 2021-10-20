import mechanicalsoup
import requests
from bs4 import BeautifulSoup
import re
import os
import time
if not os.path.exists('./NEDDb/'):
    os.makedirs('./NEDDb/')
if not os.path.exists('./Dupes/'):
    os.makedirs('./Dupes/')

b = mechanicalsoup.StatefulBrowser()
url = "https://www.nedesigns.com/rct2-objects/"

print
datNames = []
linkList = []
while True:
    try:
        print ("To avoid scanning 85 pages of 64 broken object links each, enter a value of '86' or slightly higher. Currently, when sorted by downloads ascending, all objects on pages leading up to 86 are null.")
        start = int(input("Enter page number to start on: "))
        print("To scrape all objects, enter the value of the total number of pages of objects in https://www.nedesigns.com/rct2-objects/ ('433' or higher suggested).")
        end = int(input("Enter page to end on: "))

        if start < 1 or end < 1 or start > end:
            print('Error: Invalid values entered. Please put a value greater than zero, and be sure that the starting page is less than the ending page.')
        else:
            print("Please wait. This process can take several minutes.")
            break
        print()
    except:
        print("Error: Invalid values entered. Please put a value greater than zero, and be sure that the starting page is less than the ending page.")
for i in range(start, end + 1):
    full_url = f"{url}page-{i}?order=da"
    b.open(full_url)
    ext = re.compile('.*rct2-object\/\d*\/')
    links = b.get_current_page().find_all('a')
    links = set([x.attrs['href'] for x in links if ext.match(x.attrs['href']) and str(x.attrs['href']).count('/') <= 6])
    for num, link in enumerate(links):
        surl = link
        page = requests.get(surl)
        soup = BeautifulSoup(page.content, 'html.parser')
        results = soup.find('div', {'class', "content-header-wrap"})
        contentFix = str(results.contents[1]).split('/ ')[1][:-5]

        tempLink = ''
        if '&amp;' in contentFix:
            cd = contentFix.replace('&amp;', '&')
            CC = '/' + contentFix + '/download'
            tempLink = '/'.join(link.split('/')[:-1]) + CC
            datNames.append(cd)
        else:
            tempLink = link + 'download'
            datNames.append(contentFix)

        linkList.append(tempLink)

loadingBar = '[................................................................]'
print(loadingBar)
value = len(linkList)

container = []

for num, link_url in enumerate(linkList):
    if num % int(value/ 64) == 0:
        loadingBar = loadingBar.replace('.', '|', 1)
        os.system('cls')
        print(loadingBar)
        print(str(int(num / value * 100)) + "%")

#This section is the actual downloading. Inaccessible downloads are prevented by the last 3 lines. All 404 pages on NEDesigns.com are 167,882 bytes (~169,750 bytes on disk), and only one even comes close, so this prevents that range from being accepted. This feature may become moot if NEDesigns changes the size of the html on its 404 page or base UI to exceed or drop below this range.
    file = datNames[num]
    if file not in container:
        container.append(file)
        filename = file + '.DAT'
        open("./NEDDb/" + str(datNames[num]), 'a').close
        mLink = '<a>' + link_url + '</a>'
        soup = BeautifulSoup(mLink,'html.parser')
        mLink = soup.find_all('<a>')
        r = requests.get(link_url, stream=True)
        with open("./NEDDb/" + str(datNames[num]), 'wb') as f:
            for chunk in r.iter_content(chunk_size = 1024):
                if chunk:
                    f.write(chunk)
        size = int(os.path.getsize("./NEDDb/" + str(datNames[num])))
        if size > 167880 and size < 170000:
            os.remove("./NEDDb/" + str(datNames[num]))

    else:
        container.append(file)
        filename = str(file) + '~(' + link_url.split('/')[-4].upper() + ').DAT'
        open("./Dupes/" + str(filename), 'a').close
        r = requests.get(link_url, stream=True)
        with open("./Dupes/" + str(filename), 'wb') as f:
            for chunk in r.iter_content(chunk_size=1024):
                if chunk:
                    f.write(chunk)
        size = int(os.path.getsize("./Dupes/" + str(filename)))
        if size > 167880 and size < 170000:
            os.remove("./NEDDb/" + str(filename))

print('[||||||||||||||||||||||||||||||||||||||||||||||||||||||||||||||||]')
print('100%')
input()

