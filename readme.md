# Quora scraper

Quora scraper (works as of Jan. 2023). The script can scrap questions from a topic (https://www.quora.com/topic/Finance -> ['https://www.quora.com/Using-technical-analysis-do-you-think-the-S-P-500', ...]) and then scrap the answers. If you already have links pointing to questions, you can leave the argument empty (see below).

The script returns the question, answers, and engagement metrics (votes, comments, shares, and views) as a .csv file and related questions as a .pkl file. 

## Scraping options

### Example

```
if __name__ == "__main__":
    main(topics=['China', 'Economics'], save_dir="C:/data/quora/")
```

### topics=None 

Expected input: list. Example: ['Computer_science', 'Physics']

### question_links=None 
Expected input: list. Links to questions if you already scraped topics or are using data from your own sources.

### save_dir = None
Expected input: str. Save directory.

### save_frequency_main=100 
Expected input: int. Save when the number of questions scraped >= than this value. Set lower if you have an unstable internet connection, higher if you want fewer but larger files.


### previous_save_number=0
Expected input: int. When the script saves questions, the total number of questions scraped so far is part of the save name. If the program hangs for any reason, you can resume scraping in the same dir without rewriting your old work

### get_views=False

Due to Quora's anti-scraping measures, we have to go through hoops to get the viewcount. This makes the program unstable, which is why when get_views=True, we use the multiprocessing module to timeout the script as it has a 6% failure rate. This means much slower scraping. Consider leaving this as False or running several scripts at the same time if you need the views.

When get_views=False, the program is much faster as it starts with a new question as soon as it finishes scraping the previous page.

## Important notice
get_views=True results in much slower scraping. If you find a way to evade the antiscraping algo or have an idea to improve efficiency, please feel free to make a pull request!

## License
Attribution-NonCommercial 3.0 Unported (CC BY-NC 3.0) 

https://creativecommons.org/licenses/by-nc/3.0/
