<template>
  <div id="app">
    <!-- <HelloWorld msg="Welcome to Your Vue.js App"/> -->
    <div id='container'>
      <page-title :site-name=siteName />
      <div id='tagList'>
        <TagOption @changeTag=changeTag :tag=tag :filteredTag=filteredTag v-for='tag in tagOptions' :key='tag.id' />
      </div>
      <div id='itemList'>
        <ListItem :item=item :filteredTag=filteredTag v-for='item in listItems' :key='item.id' />
      </div>
      <!-- <div id='inputDiv'>
        <input type='text' class='inputText' id='itemImageUrlInput' value='icon'>
        <input type='button' @click = 'addItem' id='itemAddButton' value='add item' />
        <input type='text' class='inputText' id='itemNameInput' value='text'>
      </div> -->
      <author-info />
    </div>
  </div>
</template>

<script>
import TagOption from './components/TagOption.vue'
import ListItem from './components/ListItem.vue'
import PageTitle from './components/PageTitle.vue'
import AuthorInfo from './components/AuthorInfo.vue'

export default {
  name: 'App',
  components: {
    ListItem,
    PageTitle,
    AuthorInfo,
    TagOption
  },
  data: function(){
    let unindexedItems = [
      {
        url: 'https://dev-bpm86-005.ibpmpro.srv:9443/ProcessCenter',
        imageSrc: 'ibm bpm',
        text: 'Process Center',
        tags: ['frontend', 'backend']
      }, {
        url: 'https://www.postgresql.org',
        imageSrc: 'www.postgresql.org',
        text: 'PostgreSQL',
        tags: ['databases']
      }, {
        url: 'https://www.pgadmin.org',
        imageSrc: 'www.pgadmin.org',
        text: 'pgAdmin',
        tags: ['databases']
      }, {
        url: 'https://lucene.apache.org',
        imageSrc: 'lucene.apache.org',
        text: 'Lucene',
        tags: ['databases']
      }, {
        url: 'https://vuejs.org/',
        imageSrc: 'vuejs.org',
        text: 'Vue.js',
        tags: ['frontend']
      }, {
        url: 'https://en.wikipedia.org/wiki/JavaScript',
        imageSrc: 'javascript',
        text: 'Javascript',
        tags: ['frontend', 'backend']
      }, {
        url: 'https://www.w3.org/standards/webdesign/htmlcss#whathtml',
        imageSrc: 'html',
        text: 'HTML',
        tags: ['frontend']
      }, {
        url: 'https://www.w3.org/standards/webdesign/htmlcss#whatcss',
        imageSrc: 'css',
        text: 'CSS',
        tags: ['frontend']
      }, {
        url: 'https://hgdb.org/confluence/',
        imageSrc: 'mercury',
        text: 'Mercury (HgDB)',
        tags: ['databases']
      }, {
        url: 'www.soapui.org',
        imageSrc: 'www.soapui.org',
        text: 'SoapUi',
        tags: ['databases']
      }
    ];
    let unindexedTags = [
      {
        imageSrc: 'all',
        text: 'all',
      },
      {
        imageSrc: 'frontend',
        text: 'frontend',
      },
      {
        imageSrc: 'backend',
        text: 'backend',
      },
      {
        imageSrc: 'databases',
        text: 'databases',
      },
    ]
    let listItems = []
    for(let element of unindexedItems){
      let nextObject = {
        index: listItems.length,
        url: element.url,
        imageSrc: element.imageSrc,
        text: element.text,
        tags: element.tags
      }
      listItems.push(nextObject)
    }
    let tagOptions = []
    for(let tag of unindexedTags){
      let nextTag = {
        index: tagOptions.length,
        imageSrc: tag.imageSrc,
        text: tag.text
      }
      tagOptions.push(nextTag)
    }
    return {
      siteName: 'Technologies',
      listItems,
      tagOptions,
      filteredTag: 'all'
    }
  },
  methods: {
    addItem: function () {
      this.listItems.push({
          index: this.listItems.length,
          imageSrc: document.getElementById('itemImageUrlInput').value,
          text: document.getElementById('itemNameInput').value
        })
    },
    changeTag: function (tag) {
      this.filteredTag = tag
    }
  }
}

</script>

<style>




@keyframes backgroundloop {
0.0% { --main-hue: 0.0; }
0.1% { --main-hue: 0.36; }
0.2% { --main-hue: 0.72; }
0.3% { --main-hue: 1.08; }
0.4% { --main-hue: 1.44; }
0.5% { --main-hue: 1.8; }
0.6% { --main-hue: 2.16; }
0.7% { --main-hue: 2.52; }
0.8% { --main-hue: 2.88; }
0.9% { --main-hue: 3.24; }
1.0% { --main-hue: 3.6; }
1.1% { --main-hue: 3.96; }
1.2% { --main-hue: 4.32; }
1.3% { --main-hue: 4.68; }
1.4% { --main-hue: 5.04; }
1.5% { --main-hue: 5.4; }
1.6% { --main-hue: 5.76; }
1.7% { --main-hue: 6.12; }
1.8% { --main-hue: 6.48; }
1.9% { --main-hue: 6.84; }
2.0% { --main-hue: 7.2; }
2.1% { --main-hue: 7.56; }
2.2% { --main-hue: 7.92; }
2.3% { --main-hue: 8.28; }
2.4% { --main-hue: 8.64; }
2.5% { --main-hue: 9.0; }
2.6% { --main-hue: 9.36; }
2.7% { --main-hue: 9.72; }
2.8% { --main-hue: 10.08; }
2.9% { --main-hue: 10.44; }
3.0% { --main-hue: 10.8; }
3.1% { --main-hue: 11.16; }
3.2% { --main-hue: 11.52; }
3.3% { --main-hue: 11.88; }
3.4% { --main-hue: 12.24; }
3.5% { --main-hue: 12.6; }
3.6% { --main-hue: 12.96; }
3.7% { --main-hue: 13.32; }
3.8% { --main-hue: 13.68; }
3.9% { --main-hue: 14.04; }
4.0% { --main-hue: 14.4; }
4.1% { --main-hue: 14.76; }
4.2% { --main-hue: 15.12; }
4.3% { --main-hue: 15.48; }
4.4% { --main-hue: 15.84; }
4.5% { --main-hue: 16.2; }
4.6% { --main-hue: 16.56; }
4.7% { --main-hue: 16.92; }
4.8% { --main-hue: 17.28; }
4.9% { --main-hue: 17.64; }
5.0% { --main-hue: 18.0; }
5.1% { --main-hue: 18.36; }
5.2% { --main-hue: 18.72; }
5.3% { --main-hue: 19.08; }
5.4% { --main-hue: 19.44; }
5.5% { --main-hue: 19.8; }
5.6% { --main-hue: 20.16; }
5.7% { --main-hue: 20.52; }
5.8% { --main-hue: 20.88; }
5.9% { --main-hue: 21.24; }
6.0% { --main-hue: 21.6; }
6.1% { --main-hue: 21.96; }
6.2% { --main-hue: 22.32; }
6.3% { --main-hue: 22.68; }
6.4% { --main-hue: 23.04; }
6.5% { --main-hue: 23.4; }
6.6% { --main-hue: 23.76; }
6.7% { --main-hue: 24.12; }
6.8% { --main-hue: 24.48; }
6.9% { --main-hue: 24.84; }
7.0% { --main-hue: 25.2; }
7.1% { --main-hue: 25.56; }
7.2% { --main-hue: 25.92; }
7.3% { --main-hue: 26.28; }
7.4% { --main-hue: 26.64; }
7.5% { --main-hue: 27.0; }
7.6% { --main-hue: 27.36; }
7.7% { --main-hue: 27.72; }
7.8% { --main-hue: 28.08; }
7.9% { --main-hue: 28.44; }
8.0% { --main-hue: 28.8; }
8.1% { --main-hue: 29.16; }
8.2% { --main-hue: 29.52; }
8.3% { --main-hue: 29.88; }
8.4% { --main-hue: 30.24; }
8.5% { --main-hue: 30.6; }
8.6% { --main-hue: 30.96; }
8.7% { --main-hue: 31.32; }
8.8% { --main-hue: 31.68; }
8.9% { --main-hue: 32.04; }
9.0% { --main-hue: 32.4; }
9.1% { --main-hue: 32.76; }
9.2% { --main-hue: 33.12; }
9.3% { --main-hue: 33.48; }
9.4% { --main-hue: 33.84; }
9.5% { --main-hue: 34.2; }
9.6% { --main-hue: 34.56; }
9.7% { --main-hue: 34.92; }
9.8% { --main-hue: 35.28; }
9.9% { --main-hue: 35.64; }
10.0% { --main-hue: 36.0; }
10.1% { --main-hue: 36.36; }
10.2% { --main-hue: 36.72; }
10.3% { --main-hue: 37.08; }
10.4% { --main-hue: 37.44; }
10.5% { --main-hue: 37.8; }
10.6% { --main-hue: 38.16; }
10.7% { --main-hue: 38.52; }
10.8% { --main-hue: 38.88; }
10.9% { --main-hue: 39.24; }
11.0% { --main-hue: 39.6; }
11.1% { --main-hue: 39.96; }
11.2% { --main-hue: 40.32; }
11.3% { --main-hue: 40.68; }
11.4% { --main-hue: 41.04; }
11.5% { --main-hue: 41.4; }
11.6% { --main-hue: 41.76; }
11.7% { --main-hue: 42.12; }
11.8% { --main-hue: 42.48; }
11.9% { --main-hue: 42.84; }
12.0% { --main-hue: 43.2; }
12.1% { --main-hue: 43.56; }
12.2% { --main-hue: 43.92; }
12.3% { --main-hue: 44.28; }
12.4% { --main-hue: 44.64; }
12.5% { --main-hue: 45.0; }
12.6% { --main-hue: 45.36; }
12.7% { --main-hue: 45.72; }
12.8% { --main-hue: 46.08; }
12.9% { --main-hue: 46.44; }
13.0% { --main-hue: 46.8; }
13.1% { --main-hue: 47.16; }
13.2% { --main-hue: 47.52; }
13.3% { --main-hue: 47.88; }
13.4% { --main-hue: 48.24; }
13.5% { --main-hue: 48.6; }
13.6% { --main-hue: 48.96; }
13.7% { --main-hue: 49.32; }
13.8% { --main-hue: 49.68; }
13.9% { --main-hue: 50.04; }
14.0% { --main-hue: 50.4; }
14.1% { --main-hue: 50.76; }
14.2% { --main-hue: 51.12; }
14.3% { --main-hue: 51.48; }
14.4% { --main-hue: 51.84; }
14.5% { --main-hue: 52.2; }
14.6% { --main-hue: 52.56; }
14.7% { --main-hue: 52.92; }
14.8% { --main-hue: 53.28; }
14.9% { --main-hue: 53.64; }
15.0% { --main-hue: 54.0; }
15.1% { --main-hue: 54.36; }
15.2% { --main-hue: 54.72; }
15.3% { --main-hue: 55.08; }
15.4% { --main-hue: 55.44; }
15.5% { --main-hue: 55.8; }
15.6% { --main-hue: 56.16; }
15.7% { --main-hue: 56.52; }
15.8% { --main-hue: 56.88; }
15.9% { --main-hue: 57.24; }
16.0% { --main-hue: 57.6; }
16.1% { --main-hue: 57.96; }
16.2% { --main-hue: 58.32; }
16.3% { --main-hue: 58.68; }
16.4% { --main-hue: 59.04; }
16.5% { --main-hue: 59.4; }
16.6% { --main-hue: 59.76; }
16.7% { --main-hue: 60.12; }
16.8% { --main-hue: 60.48; }
16.9% { --main-hue: 60.84; }
17.0% { --main-hue: 61.2; }
17.1% { --main-hue: 61.56; }
17.2% { --main-hue: 61.92; }
17.3% { --main-hue: 62.28; }
17.4% { --main-hue: 62.64; }
17.5% { --main-hue: 63.0; }
17.6% { --main-hue: 63.36; }
17.7% { --main-hue: 63.72; }
17.8% { --main-hue: 64.08; }
17.9% { --main-hue: 64.44; }
18.0% { --main-hue: 64.8; }
18.1% { --main-hue: 65.16; }
18.2% { --main-hue: 65.52; }
18.3% { --main-hue: 65.88; }
18.4% { --main-hue: 66.24; }
18.5% { --main-hue: 66.6; }
18.6% { --main-hue: 66.96; }
18.7% { --main-hue: 67.32; }
18.8% { --main-hue: 67.68; }
18.9% { --main-hue: 68.04; }
19.0% { --main-hue: 68.4; }
19.1% { --main-hue: 68.76; }
19.2% { --main-hue: 69.12; }
19.3% { --main-hue: 69.48; }
19.4% { --main-hue: 69.84; }
19.5% { --main-hue: 70.2; }
19.6% { --main-hue: 70.56; }
19.7% { --main-hue: 70.92; }
19.8% { --main-hue: 71.28; }
19.9% { --main-hue: 71.64; }
20.0% { --main-hue: 72.0; }
20.1% { --main-hue: 72.36; }
20.2% { --main-hue: 72.72; }
20.3% { --main-hue: 73.08; }
20.4% { --main-hue: 73.44; }
20.5% { --main-hue: 73.8; }
20.6% { --main-hue: 74.16; }
20.7% { --main-hue: 74.52; }
20.8% { --main-hue: 74.88; }
20.9% { --main-hue: 75.24; }
21.0% { --main-hue: 75.6; }
21.1% { --main-hue: 75.96; }
21.2% { --main-hue: 76.32; }
21.3% { --main-hue: 76.68; }
21.4% { --main-hue: 77.04; }
21.5% { --main-hue: 77.4; }
21.6% { --main-hue: 77.76; }
21.7% { --main-hue: 78.12; }
21.8% { --main-hue: 78.48; }
21.9% { --main-hue: 78.84; }
22.0% { --main-hue: 79.2; }
22.1% { --main-hue: 79.56; }
22.2% { --main-hue: 79.92; }
22.3% { --main-hue: 80.28; }
22.4% { --main-hue: 80.64; }
22.5% { --main-hue: 81.0; }
22.6% { --main-hue: 81.36; }
22.7% { --main-hue: 81.72; }
22.8% { --main-hue: 82.08; }
22.9% { --main-hue: 82.44; }
23.0% { --main-hue: 82.8; }
23.1% { --main-hue: 83.16; }
23.2% { --main-hue: 83.52; }
23.3% { --main-hue: 83.88; }
23.4% { --main-hue: 84.24; }
23.5% { --main-hue: 84.6; }
23.6% { --main-hue: 84.96; }
23.7% { --main-hue: 85.32; }
23.8% { --main-hue: 85.68; }
23.9% { --main-hue: 86.04; }
24.0% { --main-hue: 86.4; }
24.1% { --main-hue: 86.76; }
24.2% { --main-hue: 87.12; }
24.3% { --main-hue: 87.48; }
24.4% { --main-hue: 87.84; }
24.5% { --main-hue: 88.2; }
24.6% { --main-hue: 88.56; }
24.7% { --main-hue: 88.92; }
24.8% { --main-hue: 89.28; }
24.9% { --main-hue: 89.64; }
25.0% { --main-hue: 90.0; }
25.1% { --main-hue: 90.36; }
25.2% { --main-hue: 90.72; }
25.3% { --main-hue: 91.08; }
25.4% { --main-hue: 91.44; }
25.5% { --main-hue: 91.8; }
25.6% { --main-hue: 92.16; }
25.7% { --main-hue: 92.52; }
25.8% { --main-hue: 92.88; }
25.9% { --main-hue: 93.24; }
26.0% { --main-hue: 93.6; }
26.1% { --main-hue: 93.96; }
26.2% { --main-hue: 94.32; }
26.3% { --main-hue: 94.68; }
26.4% { --main-hue: 95.04; }
26.5% { --main-hue: 95.4; }
26.6% { --main-hue: 95.76; }
26.7% { --main-hue: 96.12; }
26.8% { --main-hue: 96.48; }
26.9% { --main-hue: 96.84; }
27.0% { --main-hue: 97.2; }
27.1% { --main-hue: 97.56; }
27.2% { --main-hue: 97.92; }
27.3% { --main-hue: 98.28; }
27.4% { --main-hue: 98.64; }
27.5% { --main-hue: 99.0; }
27.6% { --main-hue: 99.36; }
27.7% { --main-hue: 99.72; }
27.8% { --main-hue: 100.08; }
27.9% { --main-hue: 100.44; }
28.0% { --main-hue: 100.8; }
28.1% { --main-hue: 101.16; }
28.2% { --main-hue: 101.52; }
28.3% { --main-hue: 101.88; }
28.4% { --main-hue: 102.24; }
28.5% { --main-hue: 102.6; }
28.6% { --main-hue: 102.96; }
28.7% { --main-hue: 103.32; }
28.8% { --main-hue: 103.68; }
28.9% { --main-hue: 104.04; }
29.0% { --main-hue: 104.4; }
29.1% { --main-hue: 104.76; }
29.2% { --main-hue: 105.12; }
29.3% { --main-hue: 105.48; }
29.4% { --main-hue: 105.84; }
29.5% { --main-hue: 106.2; }
29.6% { --main-hue: 106.56; }
29.7% { --main-hue: 106.92; }
29.8% { --main-hue: 107.28; }
29.9% { --main-hue: 107.64; }
30.0% { --main-hue: 108.0; }
30.1% { --main-hue: 108.36; }
30.2% { --main-hue: 108.72; }
30.3% { --main-hue: 109.08; }
30.4% { --main-hue: 109.44; }
30.5% { --main-hue: 109.8; }
30.6% { --main-hue: 110.16; }
30.7% { --main-hue: 110.52; }
30.8% { --main-hue: 110.88; }
30.9% { --main-hue: 111.24; }
31.0% { --main-hue: 111.6; }
31.1% { --main-hue: 111.96; }
31.2% { --main-hue: 112.32; }
31.3% { --main-hue: 112.68; }
31.4% { --main-hue: 113.04; }
31.5% { --main-hue: 113.4; }
31.6% { --main-hue: 113.76; }
31.7% { --main-hue: 114.12; }
31.8% { --main-hue: 114.48; }
31.9% { --main-hue: 114.84; }
32.0% { --main-hue: 115.2; }
32.1% { --main-hue: 115.56; }
32.2% { --main-hue: 115.92; }
32.3% { --main-hue: 116.28; }
32.4% { --main-hue: 116.64; }
32.5% { --main-hue: 117.0; }
32.6% { --main-hue: 117.36; }
32.7% { --main-hue: 117.72; }
32.8% { --main-hue: 118.08; }
32.9% { --main-hue: 118.44; }
33.0% { --main-hue: 118.8; }
33.1% { --main-hue: 119.16; }
33.2% { --main-hue: 119.52; }
33.3% { --main-hue: 119.88; }
33.4% { --main-hue: 120.24; }
33.5% { --main-hue: 120.6; }
33.6% { --main-hue: 120.96; }
33.7% { --main-hue: 121.32; }
33.8% { --main-hue: 121.68; }
33.9% { --main-hue: 122.04; }
34.0% { --main-hue: 122.4; }
34.1% { --main-hue: 122.76; }
34.2% { --main-hue: 123.12; }
34.3% { --main-hue: 123.48; }
34.4% { --main-hue: 123.84; }
34.5% { --main-hue: 124.2; }
34.6% { --main-hue: 124.56; }
34.7% { --main-hue: 124.92; }
34.8% { --main-hue: 125.28; }
34.9% { --main-hue: 125.64; }
35.0% { --main-hue: 126.0; }
35.1% { --main-hue: 126.36; }
35.2% { --main-hue: 126.72; }
35.3% { --main-hue: 127.08; }
35.4% { --main-hue: 127.44; }
35.5% { --main-hue: 127.8; }
35.6% { --main-hue: 128.16; }
35.7% { --main-hue: 128.52; }
35.8% { --main-hue: 128.88; }
35.9% { --main-hue: 129.24; }
36.0% { --main-hue: 129.6; }
36.1% { --main-hue: 129.96; }
36.2% { --main-hue: 130.32; }
36.3% { --main-hue: 130.68; }
36.4% { --main-hue: 131.04; }
36.5% { --main-hue: 131.4; }
36.6% { --main-hue: 131.76; }
36.7% { --main-hue: 132.12; }
36.8% { --main-hue: 132.48; }
36.9% { --main-hue: 132.84; }
37.0% { --main-hue: 133.2; }
37.1% { --main-hue: 133.56; }
37.2% { --main-hue: 133.92; }
37.3% { --main-hue: 134.28; }
37.4% { --main-hue: 134.64; }
37.5% { --main-hue: 135.0; }
37.6% { --main-hue: 135.36; }
37.7% { --main-hue: 135.72; }
37.8% { --main-hue: 136.08; }
37.9% { --main-hue: 136.44; }
38.0% { --main-hue: 136.8; }
38.1% { --main-hue: 137.16; }
38.2% { --main-hue: 137.52; }
38.3% { --main-hue: 137.88; }
38.4% { --main-hue: 138.24; }
38.5% { --main-hue: 138.6; }
38.6% { --main-hue: 138.96; }
38.7% { --main-hue: 139.32; }
38.8% { --main-hue: 139.68; }
38.9% { --main-hue: 140.04; }
39.0% { --main-hue: 140.4; }
39.1% { --main-hue: 140.76; }
39.2% { --main-hue: 141.12; }
39.3% { --main-hue: 141.48; }
39.4% { --main-hue: 141.84; }
39.5% { --main-hue: 142.2; }
39.6% { --main-hue: 142.56; }
39.7% { --main-hue: 142.92; }
39.8% { --main-hue: 143.28; }
39.9% { --main-hue: 143.64; }
40.0% { --main-hue: 144.0; }
40.1% { --main-hue: 144.36; }
40.2% { --main-hue: 144.72; }
40.3% { --main-hue: 145.08; }
40.4% { --main-hue: 145.44; }
40.5% { --main-hue: 145.8; }
40.6% { --main-hue: 146.16; }
40.7% { --main-hue: 146.52; }
40.8% { --main-hue: 146.88; }
40.9% { --main-hue: 147.24; }
41.0% { --main-hue: 147.6; }
41.1% { --main-hue: 147.96; }
41.2% { --main-hue: 148.32; }
41.3% { --main-hue: 148.68; }
41.4% { --main-hue: 149.04; }
41.5% { --main-hue: 149.4; }
41.6% { --main-hue: 149.76; }
41.7% { --main-hue: 150.12; }
41.8% { --main-hue: 150.48; }
41.9% { --main-hue: 150.84; }
42.0% { --main-hue: 151.2; }
42.1% { --main-hue: 151.56; }
42.2% { --main-hue: 151.92; }
42.3% { --main-hue: 152.28; }
42.4% { --main-hue: 152.64; }
42.5% { --main-hue: 153.0; }
42.6% { --main-hue: 153.36; }
42.7% { --main-hue: 153.72; }
42.8% { --main-hue: 154.08; }
42.9% { --main-hue: 154.44; }
43.0% { --main-hue: 154.8; }
43.1% { --main-hue: 155.16; }
43.2% { --main-hue: 155.52; }
43.3% { --main-hue: 155.88; }
43.4% { --main-hue: 156.24; }
43.5% { --main-hue: 156.6; }
43.6% { --main-hue: 156.96; }
43.7% { --main-hue: 157.32; }
43.8% { --main-hue: 157.68; }
43.9% { --main-hue: 158.04; }
44.0% { --main-hue: 158.4; }
44.1% { --main-hue: 158.76; }
44.2% { --main-hue: 159.12; }
44.3% { --main-hue: 159.48; }
44.4% { --main-hue: 159.84; }
44.5% { --main-hue: 160.2; }
44.6% { --main-hue: 160.56; }
44.7% { --main-hue: 160.92; }
44.8% { --main-hue: 161.28; }
44.9% { --main-hue: 161.64; }
45.0% { --main-hue: 162.0; }
45.1% { --main-hue: 162.36; }
45.2% { --main-hue: 162.72; }
45.3% { --main-hue: 163.08; }
45.4% { --main-hue: 163.44; }
45.5% { --main-hue: 163.8; }
45.6% { --main-hue: 164.16; }
45.7% { --main-hue: 164.52; }
45.8% { --main-hue: 164.88; }
45.9% { --main-hue: 165.24; }
46.0% { --main-hue: 165.6; }
46.1% { --main-hue: 165.96; }
46.2% { --main-hue: 166.32; }
46.3% { --main-hue: 166.68; }
46.4% { --main-hue: 167.04; }
46.5% { --main-hue: 167.4; }
46.6% { --main-hue: 167.76; }
46.7% { --main-hue: 168.12; }
46.8% { --main-hue: 168.48; }
46.9% { --main-hue: 168.84; }
47.0% { --main-hue: 169.2; }
47.1% { --main-hue: 169.56; }
47.2% { --main-hue: 169.92; }
47.3% { --main-hue: 170.28; }
47.4% { --main-hue: 170.64; }
47.5% { --main-hue: 171.0; }
47.6% { --main-hue: 171.36; }
47.7% { --main-hue: 171.72; }
47.8% { --main-hue: 172.08; }
47.9% { --main-hue: 172.44; }
48.0% { --main-hue: 172.8; }
48.1% { --main-hue: 173.16; }
48.2% { --main-hue: 173.52; }
48.3% { --main-hue: 173.88; }
48.4% { --main-hue: 174.24; }
48.5% { --main-hue: 174.6; }
48.6% { --main-hue: 174.96; }
48.7% { --main-hue: 175.32; }
48.8% { --main-hue: 175.68; }
48.9% { --main-hue: 176.04; }
49.0% { --main-hue: 176.4; }
49.1% { --main-hue: 176.76; }
49.2% { --main-hue: 177.12; }
49.3% { --main-hue: 177.48; }
49.4% { --main-hue: 177.84; }
49.5% { --main-hue: 178.2; }
49.6% { --main-hue: 178.56; }
49.7% { --main-hue: 178.92; }
49.8% { --main-hue: 179.28; }
49.9% { --main-hue: 179.64; }
50.0% { --main-hue: 180.0; }
50.1% { --main-hue: 180.36; }
50.2% { --main-hue: 180.72; }
50.3% { --main-hue: 181.08; }
50.4% { --main-hue: 181.44; }
50.5% { --main-hue: 181.8; }
50.6% { --main-hue: 182.16; }
50.7% { --main-hue: 182.52; }
50.8% { --main-hue: 182.88; }
50.9% { --main-hue: 183.24; }
51.0% { --main-hue: 183.6; }
51.1% { --main-hue: 183.96; }
51.2% { --main-hue: 184.32; }
51.3% { --main-hue: 184.68; }
51.4% { --main-hue: 185.04; }
51.5% { --main-hue: 185.4; }
51.6% { --main-hue: 185.76; }
51.7% { --main-hue: 186.12; }
51.8% { --main-hue: 186.48; }
51.9% { --main-hue: 186.84; }
52.0% { --main-hue: 187.2; }
52.1% { --main-hue: 187.56; }
52.2% { --main-hue: 187.92; }
52.3% { --main-hue: 188.28; }
52.4% { --main-hue: 188.64; }
52.5% { --main-hue: 189.0; }
52.6% { --main-hue: 189.36; }
52.7% { --main-hue: 189.72; }
52.8% { --main-hue: 190.08; }
52.9% { --main-hue: 190.44; }
53.0% { --main-hue: 190.8; }
53.1% { --main-hue: 191.16; }
53.2% { --main-hue: 191.52; }
53.3% { --main-hue: 191.88; }
53.4% { --main-hue: 192.24; }
53.5% { --main-hue: 192.6; }
53.6% { --main-hue: 192.96; }
53.7% { --main-hue: 193.32; }
53.8% { --main-hue: 193.68; }
53.9% { --main-hue: 194.04; }
54.0% { --main-hue: 194.4; }
54.1% { --main-hue: 194.76; }
54.2% { --main-hue: 195.12; }
54.3% { --main-hue: 195.48; }
54.4% { --main-hue: 195.84; }
54.5% { --main-hue: 196.2; }
54.6% { --main-hue: 196.56; }
54.7% { --main-hue: 196.92; }
54.8% { --main-hue: 197.28; }
54.9% { --main-hue: 197.64; }
55.0% { --main-hue: 198.0; }
55.1% { --main-hue: 198.36; }
55.2% { --main-hue: 198.72; }
55.3% { --main-hue: 199.08; }
55.4% { --main-hue: 199.44; }
55.5% { --main-hue: 199.8; }
55.6% { --main-hue: 200.16; }
55.7% { --main-hue: 200.52; }
55.8% { --main-hue: 200.88; }
55.9% { --main-hue: 201.24; }
56.0% { --main-hue: 201.6; }
56.1% { --main-hue: 201.96; }
56.2% { --main-hue: 202.32; }
56.3% { --main-hue: 202.68; }
56.4% { --main-hue: 203.04; }
56.5% { --main-hue: 203.4; }
56.6% { --main-hue: 203.76; }
56.7% { --main-hue: 204.12; }
56.8% { --main-hue: 204.48; }
56.9% { --main-hue: 204.84; }
57.0% { --main-hue: 205.2; }
57.1% { --main-hue: 205.56; }
57.2% { --main-hue: 205.92; }
57.3% { --main-hue: 206.28; }
57.4% { --main-hue: 206.64; }
57.5% { --main-hue: 207.0; }
57.6% { --main-hue: 207.36; }
57.7% { --main-hue: 207.72; }
57.8% { --main-hue: 208.08; }
57.9% { --main-hue: 208.44; }
58.0% { --main-hue: 208.8; }
58.1% { --main-hue: 209.16; }
58.2% { --main-hue: 209.52; }
58.3% { --main-hue: 209.88; }
58.4% { --main-hue: 210.24; }
58.5% { --main-hue: 210.6; }
58.6% { --main-hue: 210.96; }
58.7% { --main-hue: 211.32; }
58.8% { --main-hue: 211.68; }
58.9% { --main-hue: 212.04; }
59.0% { --main-hue: 212.4; }
59.1% { --main-hue: 212.76; }
59.2% { --main-hue: 213.12; }
59.3% { --main-hue: 213.48; }
59.4% { --main-hue: 213.84; }
59.5% { --main-hue: 214.2; }
59.6% { --main-hue: 214.56; }
59.7% { --main-hue: 214.92; }
59.8% { --main-hue: 215.28; }
59.9% { --main-hue: 215.64; }
60.0% { --main-hue: 216.0; }
60.1% { --main-hue: 216.36; }
60.2% { --main-hue: 216.72; }
60.3% { --main-hue: 217.08; }
60.4% { --main-hue: 217.44; }
60.5% { --main-hue: 217.8; }
60.6% { --main-hue: 218.16; }
60.7% { --main-hue: 218.52; }
60.8% { --main-hue: 218.88; }
60.9% { --main-hue: 219.24; }
61.0% { --main-hue: 219.6; }
61.1% { --main-hue: 219.96; }
61.2% { --main-hue: 220.32; }
61.3% { --main-hue: 220.68; }
61.4% { --main-hue: 221.04; }
61.5% { --main-hue: 221.4; }
61.6% { --main-hue: 221.76; }
61.7% { --main-hue: 222.12; }
61.8% { --main-hue: 222.48; }
61.9% { --main-hue: 222.84; }
62.0% { --main-hue: 223.2; }
62.1% { --main-hue: 223.56; }
62.2% { --main-hue: 223.92; }
62.3% { --main-hue: 224.28; }
62.4% { --main-hue: 224.64; }
62.5% { --main-hue: 225.0; }
62.6% { --main-hue: 225.36; }
62.7% { --main-hue: 225.72; }
62.8% { --main-hue: 226.08; }
62.9% { --main-hue: 226.44; }
63.0% { --main-hue: 226.8; }
63.1% { --main-hue: 227.16; }
63.2% { --main-hue: 227.52; }
63.3% { --main-hue: 227.88; }
63.4% { --main-hue: 228.24; }
63.5% { --main-hue: 228.6; }
63.6% { --main-hue: 228.96; }
63.7% { --main-hue: 229.32; }
63.8% { --main-hue: 229.68; }
63.9% { --main-hue: 230.04; }
64.0% { --main-hue: 230.4; }
64.1% { --main-hue: 230.76; }
64.2% { --main-hue: 231.12; }
64.3% { --main-hue: 231.48; }
64.4% { --main-hue: 231.84; }
64.5% { --main-hue: 232.2; }
64.6% { --main-hue: 232.56; }
64.7% { --main-hue: 232.92; }
64.8% { --main-hue: 233.28; }
64.9% { --main-hue: 233.64; }
65.0% { --main-hue: 234.0; }
65.1% { --main-hue: 234.36; }
65.2% { --main-hue: 234.72; }
65.3% { --main-hue: 235.08; }
65.4% { --main-hue: 235.44; }
65.5% { --main-hue: 235.8; }
65.6% { --main-hue: 236.16; }
65.7% { --main-hue: 236.52; }
65.8% { --main-hue: 236.88; }
65.9% { --main-hue: 237.24; }
66.0% { --main-hue: 237.6; }
66.1% { --main-hue: 237.96; }
66.2% { --main-hue: 238.32; }
66.3% { --main-hue: 238.68; }
66.4% { --main-hue: 239.04; }
66.5% { --main-hue: 239.4; }
66.6% { --main-hue: 239.76; }
66.7% { --main-hue: 240.12; }
66.8% { --main-hue: 240.48; }
66.9% { --main-hue: 240.84; }
67.0% { --main-hue: 241.2; }
67.1% { --main-hue: 241.56; }
67.2% { --main-hue: 241.92; }
67.3% { --main-hue: 242.28; }
67.4% { --main-hue: 242.64; }
67.5% { --main-hue: 243.0; }
67.6% { --main-hue: 243.36; }
67.7% { --main-hue: 243.72; }
67.8% { --main-hue: 244.08; }
67.9% { --main-hue: 244.44; }
68.0% { --main-hue: 244.8; }
68.1% { --main-hue: 245.16; }
68.2% { --main-hue: 245.52; }
68.3% { --main-hue: 245.88; }
68.4% { --main-hue: 246.24; }
68.5% { --main-hue: 246.6; }
68.6% { --main-hue: 246.96; }
68.7% { --main-hue: 247.32; }
68.8% { --main-hue: 247.68; }
68.9% { --main-hue: 248.04; }
69.0% { --main-hue: 248.4; }
69.1% { --main-hue: 248.76; }
69.2% { --main-hue: 249.12; }
69.3% { --main-hue: 249.48; }
69.4% { --main-hue: 249.84; }
69.5% { --main-hue: 250.2; }
69.6% { --main-hue: 250.56; }
69.7% { --main-hue: 250.92; }
69.8% { --main-hue: 251.28; }
69.9% { --main-hue: 251.64; }
70.0% { --main-hue: 252.0; }
70.1% { --main-hue: 252.36; }
70.2% { --main-hue: 252.72; }
70.3% { --main-hue: 253.08; }
70.4% { --main-hue: 253.44; }
70.5% { --main-hue: 253.8; }
70.6% { --main-hue: 254.16; }
70.7% { --main-hue: 254.52; }
70.8% { --main-hue: 254.88; }
70.9% { --main-hue: 255.24; }
71.0% { --main-hue: 255.6; }
71.1% { --main-hue: 255.96; }
71.2% { --main-hue: 256.32; }
71.3% { --main-hue: 256.68; }
71.4% { --main-hue: 257.04; }
71.5% { --main-hue: 257.4; }
71.6% { --main-hue: 257.76; }
71.7% { --main-hue: 258.12; }
71.8% { --main-hue: 258.48; }
71.9% { --main-hue: 258.84; }
72.0% { --main-hue: 259.2; }
72.1% { --main-hue: 259.56; }
72.2% { --main-hue: 259.92; }
72.3% { --main-hue: 260.28; }
72.4% { --main-hue: 260.64; }
72.5% { --main-hue: 261.0; }
72.6% { --main-hue: 261.36; }
72.7% { --main-hue: 261.72; }
72.8% { --main-hue: 262.08; }
72.9% { --main-hue: 262.44; }
73.0% { --main-hue: 262.8; }
73.1% { --main-hue: 263.16; }
73.2% { --main-hue: 263.52; }
73.3% { --main-hue: 263.88; }
73.4% { --main-hue: 264.24; }
73.5% { --main-hue: 264.6; }
73.6% { --main-hue: 264.96; }
73.7% { --main-hue: 265.32; }
73.8% { --main-hue: 265.68; }
73.9% { --main-hue: 266.04; }
74.0% { --main-hue: 266.4; }
74.1% { --main-hue: 266.76; }
74.2% { --main-hue: 267.12; }
74.3% { --main-hue: 267.48; }
74.4% { --main-hue: 267.84; }
74.5% { --main-hue: 268.2; }
74.6% { --main-hue: 268.56; }
74.7% { --main-hue: 268.92; }
74.8% { --main-hue: 269.28; }
74.9% { --main-hue: 269.64; }
75.0% { --main-hue: 270.0; }
75.1% { --main-hue: 270.36; }
75.2% { --main-hue: 270.72; }
75.3% { --main-hue: 271.08; }
75.4% { --main-hue: 271.44; }
75.5% { --main-hue: 271.8; }
75.6% { --main-hue: 272.16; }
75.7% { --main-hue: 272.52; }
75.8% { --main-hue: 272.88; }
75.9% { --main-hue: 273.24; }
76.0% { --main-hue: 273.6; }
76.1% { --main-hue: 273.96; }
76.2% { --main-hue: 274.32; }
76.3% { --main-hue: 274.68; }
76.4% { --main-hue: 275.04; }
76.5% { --main-hue: 275.4; }
76.6% { --main-hue: 275.76; }
76.7% { --main-hue: 276.12; }
76.8% { --main-hue: 276.48; }
76.9% { --main-hue: 276.84; }
77.0% { --main-hue: 277.2; }
77.1% { --main-hue: 277.56; }
77.2% { --main-hue: 277.92; }
77.3% { --main-hue: 278.28; }
77.4% { --main-hue: 278.64; }
77.5% { --main-hue: 279.0; }
77.6% { --main-hue: 279.36; }
77.7% { --main-hue: 279.72; }
77.8% { --main-hue: 280.08; }
77.9% { --main-hue: 280.44; }
78.0% { --main-hue: 280.8; }
78.1% { --main-hue: 281.16; }
78.2% { --main-hue: 281.52; }
78.3% { --main-hue: 281.88; }
78.4% { --main-hue: 282.24; }
78.5% { --main-hue: 282.6; }
78.6% { --main-hue: 282.96; }
78.7% { --main-hue: 283.32; }
78.8% { --main-hue: 283.68; }
78.9% { --main-hue: 284.04; }
79.0% { --main-hue: 284.4; }
79.1% { --main-hue: 284.76; }
79.2% { --main-hue: 285.12; }
79.3% { --main-hue: 285.48; }
79.4% { --main-hue: 285.84; }
79.5% { --main-hue: 286.2; }
79.6% { --main-hue: 286.56; }
79.7% { --main-hue: 286.92; }
79.8% { --main-hue: 287.28; }
79.9% { --main-hue: 287.64; }
80.0% { --main-hue: 288.0; }
80.1% { --main-hue: 288.36; }
80.2% { --main-hue: 288.72; }
80.3% { --main-hue: 289.08; }
80.4% { --main-hue: 289.44; }
80.5% { --main-hue: 289.8; }
80.6% { --main-hue: 290.16; }
80.7% { --main-hue: 290.52; }
80.8% { --main-hue: 290.88; }
80.9% { --main-hue: 291.24; }
81.0% { --main-hue: 291.6; }
81.1% { --main-hue: 291.96; }
81.2% { --main-hue: 292.32; }
81.3% { --main-hue: 292.68; }
81.4% { --main-hue: 293.04; }
81.5% { --main-hue: 293.4; }
81.6% { --main-hue: 293.76; }
81.7% { --main-hue: 294.12; }
81.8% { --main-hue: 294.48; }
81.9% { --main-hue: 294.84; }
82.0% { --main-hue: 295.2; }
82.1% { --main-hue: 295.56; }
82.2% { --main-hue: 295.92; }
82.3% { --main-hue: 296.28; }
82.4% { --main-hue: 296.64; }
82.5% { --main-hue: 297.0; }
82.6% { --main-hue: 297.36; }
82.7% { --main-hue: 297.72; }
82.8% { --main-hue: 298.08; }
82.9% { --main-hue: 298.44; }
83.0% { --main-hue: 298.8; }
83.1% { --main-hue: 299.16; }
83.2% { --main-hue: 299.52; }
83.3% { --main-hue: 299.88; }
83.4% { --main-hue: 300.24; }
83.5% { --main-hue: 300.6; }
83.6% { --main-hue: 300.96; }
83.7% { --main-hue: 301.32; }
83.8% { --main-hue: 301.68; }
83.9% { --main-hue: 302.04; }
84.0% { --main-hue: 302.4; }
84.1% { --main-hue: 302.76; }
84.2% { --main-hue: 303.12; }
84.3% { --main-hue: 303.48; }
84.4% { --main-hue: 303.84; }
84.5% { --main-hue: 304.2; }
84.6% { --main-hue: 304.56; }
84.7% { --main-hue: 304.92; }
84.8% { --main-hue: 305.28; }
84.9% { --main-hue: 305.64; }
85.0% { --main-hue: 306.0; }
85.1% { --main-hue: 306.36; }
85.2% { --main-hue: 306.72; }
85.3% { --main-hue: 307.08; }
85.4% { --main-hue: 307.44; }
85.5% { --main-hue: 307.8; }
85.6% { --main-hue: 308.16; }
85.7% { --main-hue: 308.52; }
85.8% { --main-hue: 308.88; }
85.9% { --main-hue: 309.24; }
86.0% { --main-hue: 309.6; }
86.1% { --main-hue: 309.96; }
86.2% { --main-hue: 310.32; }
86.3% { --main-hue: 310.68; }
86.4% { --main-hue: 311.04; }
86.5% { --main-hue: 311.4; }
86.6% { --main-hue: 311.76; }
86.7% { --main-hue: 312.12; }
86.8% { --main-hue: 312.48; }
86.9% { --main-hue: 312.84; }
87.0% { --main-hue: 313.2; }
87.1% { --main-hue: 313.56; }
87.2% { --main-hue: 313.92; }
87.3% { --main-hue: 314.28; }
87.4% { --main-hue: 314.64; }
87.5% { --main-hue: 315.0; }
87.6% { --main-hue: 315.36; }
87.7% { --main-hue: 315.72; }
87.8% { --main-hue: 316.08; }
87.9% { --main-hue: 316.44; }
88.0% { --main-hue: 316.8; }
88.1% { --main-hue: 317.16; }
88.2% { --main-hue: 317.52; }
88.3% { --main-hue: 317.88; }
88.4% { --main-hue: 318.24; }
88.5% { --main-hue: 318.6; }
88.6% { --main-hue: 318.96; }
88.7% { --main-hue: 319.32; }
88.8% { --main-hue: 319.68; }
88.9% { --main-hue: 320.04; }
89.0% { --main-hue: 320.4; }
89.1% { --main-hue: 320.76; }
89.2% { --main-hue: 321.12; }
89.3% { --main-hue: 321.48; }
89.4% { --main-hue: 321.84; }
89.5% { --main-hue: 322.2; }
89.6% { --main-hue: 322.56; }
89.7% { --main-hue: 322.92; }
89.8% { --main-hue: 323.28; }
89.9% { --main-hue: 323.64; }
90.0% { --main-hue: 324.0; }
90.1% { --main-hue: 324.36; }
90.2% { --main-hue: 324.72; }
90.3% { --main-hue: 325.08; }
90.4% { --main-hue: 325.44; }
90.5% { --main-hue: 325.8; }
90.6% { --main-hue: 326.16; }
90.7% { --main-hue: 326.52; }
90.8% { --main-hue: 326.88; }
90.9% { --main-hue: 327.24; }
91.0% { --main-hue: 327.6; }
91.1% { --main-hue: 327.96; }
91.2% { --main-hue: 328.32; }
91.3% { --main-hue: 328.68; }
91.4% { --main-hue: 329.04; }
91.5% { --main-hue: 329.4; }
91.6% { --main-hue: 329.76; }
91.7% { --main-hue: 330.12; }
91.8% { --main-hue: 330.48; }
91.9% { --main-hue: 330.84; }
92.0% { --main-hue: 331.2; }
92.1% { --main-hue: 331.56; }
92.2% { --main-hue: 331.92; }
92.3% { --main-hue: 332.28; }
92.4% { --main-hue: 332.64; }
92.5% { --main-hue: 333.0; }
92.6% { --main-hue: 333.36; }
92.7% { --main-hue: 333.72; }
92.8% { --main-hue: 334.08; }
92.9% { --main-hue: 334.44; }
93.0% { --main-hue: 334.8; }
93.1% { --main-hue: 335.16; }
93.2% { --main-hue: 335.52; }
93.3% { --main-hue: 335.88; }
93.4% { --main-hue: 336.24; }
93.5% { --main-hue: 336.6; }
93.6% { --main-hue: 336.96; }
93.7% { --main-hue: 337.32; }
93.8% { --main-hue: 337.68; }
93.9% { --main-hue: 338.04; }
94.0% { --main-hue: 338.4; }
94.1% { --main-hue: 338.76; }
94.2% { --main-hue: 339.12; }
94.3% { --main-hue: 339.48; }
94.4% { --main-hue: 339.84; }
94.5% { --main-hue: 340.2; }
94.6% { --main-hue: 340.56; }
94.7% { --main-hue: 340.92; }
94.8% { --main-hue: 341.28; }
94.9% { --main-hue: 341.64; }
95.0% { --main-hue: 342.0; }
95.1% { --main-hue: 342.36; }
95.2% { --main-hue: 342.72; }
95.3% { --main-hue: 343.08; }
95.4% { --main-hue: 343.44; }
95.5% { --main-hue: 343.8; }
95.6% { --main-hue: 344.16; }
95.7% { --main-hue: 344.52; }
95.8% { --main-hue: 344.88; }
95.9% { --main-hue: 345.24; }
96.0% { --main-hue: 345.6; }
96.1% { --main-hue: 345.96; }
96.2% { --main-hue: 346.32; }
96.3% { --main-hue: 346.68; }
96.4% { --main-hue: 347.04; }
96.5% { --main-hue: 347.4; }
96.6% { --main-hue: 347.76; }
96.7% { --main-hue: 348.12; }
96.8% { --main-hue: 348.48; }
96.9% { --main-hue: 348.84; }
97.0% { --main-hue: 349.2; }
97.1% { --main-hue: 349.56; }
97.2% { --main-hue: 349.92; }
97.3% { --main-hue: 350.28; }
97.4% { --main-hue: 350.64; }
97.5% { --main-hue: 351.0; }
97.6% { --main-hue: 351.36; }
97.7% { --main-hue: 351.72; }
97.8% { --main-hue: 352.08; }
97.9% { --main-hue: 352.44; }
98.0% { --main-hue: 352.8; }
98.1% { --main-hue: 353.16; }
98.2% { --main-hue: 353.52; }
98.3% { --main-hue: 353.88; }
98.4% { --main-hue: 354.24; }
98.5% { --main-hue: 354.6; }
98.6% { --main-hue: 354.96; }
98.7% { --main-hue: 355.32; }
98.8% { --main-hue: 355.68; }
98.9% { --main-hue: 356.04; }
99.0% { --main-hue: 356.4; }
99.1% { --main-hue: 356.76; }
99.2% { --main-hue: 357.12; }
99.3% { --main-hue: 357.48; }
99.4% { --main-hue: 357.84; }
99.5% { --main-hue: 358.2; }
99.6% { --main-hue: 358.56; }
99.7% { --main-hue: 358.92; }
99.8% { --main-hue: 359.28; }
99.9% { --main-hue: 359.64; }
100.0% { --main-hue: 360.0; }
}

a:link {
    text-decoration: inherit;
    color: inherit;
    cursor: auto;
}

a:visited {
    text-decoration: inherit;
    color: inherit;
    cursor: auto;
}

:root {
  /* --main-hue: 120; */
  animation-name: backgroundloop;
  animation-duration: 36s;
  animation-iteration-count: infinite;
}
body {
  margin: 0px;
  position: absolute;
  top: 0;
  bottom: 0;
  left: 0;
  right: 0;
}
#app {
  font-family: Avenir, Helvetica, Arial, sans-serif;
  -webkit-font-smoothing: antialiased;
  -moz-osx-font-smoothing: grayscale;
  text-align: center;
  margin-top: 0px;
  display: grid;
  place-items: center;
  width: 100%;
  height: 100%;
}
#container {
  background-color: hsl(var(--main-hue), 25%, 60%);
  width: 100%;
  height: 100%;
}

#itemList {
  /* flexbox */
  display: grid;
  grid-auto-rows: auto;
  grid-template-columns: repeat(2, minmax(0, 1fr));

  padding: 2% 10%;
  
  /* flex */
  /* height: auto;
  display: flex;
  flex-wrap: wrap;
  flex-direction: row; */
  /* list w width item */
}

#tagList {
  /* flexbox */
  display: grid;
  grid-auto-rows: auto;
  grid-template-columns: repeat(4, minmax(0, 1fr));

  padding: 2% 10%;
}

#inputDiv{
  margin-top: 20px;
  padding: 5px 12%;
  display: grid;
  grid-template-columns: 60% 40%;
  grid-template-rows: 30px;
  column-gap: 2px;
  row-gap: 8px;
  grid-template-areas:
    "imageUrl button"
    "text button";
}

@media (min-width: 1000px) {
  #itemList {
    grid-template-columns: repeat(3, minmax(0, 1fr));
    padding-left: 15%;
    padding-right: 15%;
  }
  #tagList {
    padding-left: 15%;
    padding-right: 15%;
  }
  #tagDiv{
    padding-left: 25%;
    padding-right: 25%;
  }
}

@media (min-width: 1500px) {
  #itemList {
    grid-template-columns: repeat(4, minmax(0, 1fr));
    /* grid-template-columns: repeat(6, minmax(0, 1fr)); */
    padding-left: 20%;
    padding-right: 20%;
  }
  #tagList {
    padding-left: 20%;
    padding-right: 20%;
  }
  #inputDiv{
    padding-left: 35%;
    padding-right: 35%;
  }
}

.inputText{
  height: 30px;
  font-size: 25px;
}

#itemImageUrlInput {
  grid-area: imageUrl;
}

#itemNameInput {
  grid-area: text;
}

#itemAddButton {
  grid-area: button;
  grid-row: span 2;
  height: 74px;
  font-size: 25px;
  white-space: normal;
  word-break: break-word;
}

</style>
