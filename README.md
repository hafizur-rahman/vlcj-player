Prepare Playlist
--------
```$bash
pip install pytube
```

```
from pytube import YouTube 
from pytube import Playlist

lists = [
#     ('Al-Kitab Al-Asasi vol. 1', 'https://www.youtube.com/playlist?list=PLFXGXcvbZMjJT-OFZ6WjiJEzG8vUSyXGB'),
#     ('Al-Kitab Al-Asasi vol. 2', 'https://www.youtube.com/playlist?list=PLFXGXcvbZMjIlUKfEjZfjqJ38LYdPT66s'),
    ('Qasasun Nabiyyin Vol. 1', 'https://www.youtube.com/playlist?list=PL5xNtY-o3gWbvTPVSdopOmWA97mw3bfc0')
]

data = []

for item in lists:
    p = Playlist(item[1])

    for url in p.video_urls:
        yt = YouTube(url)

        data.append((item[0], yt.title, url))
    
import pandas as pd

df = pd.DataFrame(data, columns=['Category', 'Title', 'URL'])
df.to_csv('study.csv', index=False, header=None)
```

Sample output
```
Al-Kitab Al-Asasi vol. 1,Al Kitab Al Asasi Vol. 1 Lesson 1,https://www.youtube.com/watch?v=kQ0Mjg-Om94
Al-Kitab Al-Asasi vol. 1,Al Kitab Al Asasi Vol. 1 Lesson 2,https://www.youtube.com/watch?v=z18x8QvIJ5s
Al-Kitab Al-Asasi vol. 1,Al Kitab Al Asasi Vol. 1 Lesson 3,https://www.youtube.com/watch?v=GTF8aLVPASs
Al-Kitab Al-Asasi vol. 1,Al Kitab Al Asasi Vol. 1 Lesson 4,https://www.youtube.com/watch?v=9ZnyA5j9Dqs
```


Set Study Item List file
----------
While executing the Java application, set `study.items.file` properties.

Example:
```
-Dstudy.items.file=c:\\dev\\vlcj-player\\study-items.csv
```

Screenshot
----------

![vlcj-player](https://github.com/hafizur-rahman/vlcj-player/raw/master/doc/study-using-vlcj-player.png "vlcj-player")