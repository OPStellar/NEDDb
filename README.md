# New-Element Designs (Downloadable Objects) Database – "NEDDb"
NEDDb is a standalone application designed to download all the RCT2 Objects in the New-Element Designs Database (NEDDb) by a webscraping process coded in Python, integrating BeautifulSoup and MechanicalSoup.
The original code was released by DeathKontrol (https://www.nedesigns.com/topic/36639/download-all-nedesigns-rct2-objects-with-this-python-code/), and I took the liberty of getting all its shortcomings fixed (i.e. downloading broken links, bypassing objects that use special characters in the name such as 'CFEE&DNT' and 'WALL&ROO', and overwriting files of the same name) thanks to an assistant from the official Python Discord server.

# Installation Guide
Unlike previous iterations of the code, this one is as easy and simple:

1. Select a release package for your operating system
2. Unpack the archived file
3. Move the executable to the Objects folder where you normally put custom objects.
   • NOTE: Be sure that you don't have used folders named 'NEDDb' or 'Dupes' in that location, or else their content may be overwritten. Just saying.
4. Launch the executable. A Terminal or Command-Line window will open. Follow the directions.

Please note that the process can take several hours depending on how many pages of objects you choose to download.
Happy scraping!

# FAQ
Q: Why not just make a dump of all the objects?
A: I could, but the database is getting updated all the time. As long as the site layout doesn't change, this application will function properly. Thus, issues will probably not be addressed soon– unless you're willing to pay for the changes (to pay the guy who coded it).

Q: If you didn't code it, why is it free?
A: The guy who coded it told me that he wants it open for public use. Thus, we made it as user-friendly as possible with no cost.

Q: Will this download the original RCT2 files that appear on NEDesigns but can't be downloaded from the site?
A: No. Those files are not actually on the site; they're just included in the object database. Unlike all other objects, they are not .DAT files and cannot be downloaded in any way. And if they could, I'd have made sure this code wouldn't– because they're not free assets.

Q: I've downloaded everything, but not all objects can be loaded in some scenery groups! What went wrong?
A: It's important to note that while this does download all valid objects in the New-Element Designs database of RCT2 Objects, "the limit on scenery objects within the game, 252 small scenery, 128 large, 128 walls etc." will prevent you from being able to make full use of all objects in several scenery groups. The list will be so long in the object selector that you won't be able to scroll through all of it! This can't be helped until OpenRCT2 develops a new system for handling objects. If you think you can help with that, please join the development team!

# Planned Features
With time and a little money, this application can potentially gain:
• The ability to specify page-sorting order
• The ability to search for objects
• The ability to search by tags
• The function of distributing downloaded objects into folders by ONE user-specified criterion (tag, alphanumerical name, creator, etc.)
• Ability to scrape tracks and user-uploaded park saves, scenarios, etc. (more likely to be an altogether separate application, but it's not impossible if you want it enough!)
