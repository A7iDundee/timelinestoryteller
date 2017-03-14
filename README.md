# Timeline Storyteller

[Timeline Storyteller](https://timelinestoryteller.com/) is an expressive browser-based visual storytelling environment for presenting timelines.

You can use Timeline Storyteller to present different aspects of your data using a palette of timeline representations, scales, and layouts, as well as controls for filtering, highlighting, and annotation. You can export images of a timeline or assemble and record a story about your data and present it within the application.

To learn more about the research that informed this project, see [timelinesrevisited.github.io](https://timelinesrevisited.github.io/), which includes a survey of timeline tools and more than 200 bespoke timelines.

## Setup

1. Clone the main branch of this repository: `git clone https://github.com/Microsoft/timelinestoryteller.git`

2. Install [nodejs](https://nodejs.org/) and [npm](https://www.npmjs.com/).

3. Open a terminal at the root of the repository and install the required node modules listed in package.json ([express](https://www.npmjs.com/package/express) and [socket.io](https://www.npmjs.com/package/socket.io)): `npm install express`, `npm install socket.io`

4. Start the node server: `node app.js`

5. Open [localhost:8000](http://localhost:8000/)

## Preparing your data

Timeline Storyteller currently supports datasets of events in CSV, JSON, or Google Spreadsheet format.

Each event is specified by the following attributes:

- __Required__: `start_date`, date: YYYY, YYYY-MM-DD, or YYYY-MM-DD HH:MMZ formats are supported (Z necessary for specifying UTC, otherwise HH:MM will be time-zone dependent). BC dates are permitted, e.g., -27, -13800000000
- __Optional__: `end_date`, date: using same format as `start_date`
- __Optional__: `category`, a string corresponding to the category of the event (which Timeline Storyteller encodes as colour)
- __Optional__: `facet`,a string corresponding to another category of the event (which Timeline Storyteller uses to create a faceted timeline layout; `category` and `facet` can be identical if desired)
- __Optional__: `content_text`, a string description of the event (which Timeline Storyteller exposes as event annotations)

### Example event in JSON:

`{
  "start_date":"1775",
  "end_date":"1783",
  "content_text":"American Revolutionary War: an armed struggle for secession from the British Empire by the Thirteen Colonies that would subsequently become the United States.",
  "facet":"North America",
  "category":"North America"
},`

### Example event in CSV:

header row:

`start_date,end_date,content_text,facet,category`

example event row:

`1775,1783,American Revolutionary War: an armed struggle for secession from the British Empire by the Thirteen Colonies that would subsequently become the United States.,North America,North America`

## Usage

1. Load timeline data (demo dataset, JSON, CSV, Google Spreadsheet) or saved timeline story (a JSON Blob with extension .cdc; see step 6)

2. Select representation, scale, and layout

3. Edit the canvas

	* Click on events to annotate with their `content_text` label; resize and reposition labels; SHIFT + click to highlight events without showing label

	* Annotate with captions and images; resize and reposition captions and images

 	* Filter events by category, facet, or segment. Filter by highlighting emphasizing matching events (de-emphasizing non-matching events), or by hiding non-matching events

4. Record current canvas as a scene, which retains labels, captions, and images. Enter playback mode, navigate to previous / next recorded scene

5. Export current canvas as a PNG, SVG.

6. Export the scenes as an animated GIF or as a JSON Blob (.cdc extension)


## Demo dataset provenance

- [Priestley's Chart of Biography](https://upload.wikimedia.org/wikipedia/commons/9/98/PriestleyChart.gif)
- [Great Philosophers since the 8th Century BC](http://bl.ocks.org/rengel-de/5603464)
- [History's Largest Empires](http://nowherenearithaca.github.io/empires/index.html)
- [East Asian Dynasties](http://bl.ocks.org/bunkat/2338034)
- [Epidemics since the 14th Century](https://en.wikipedia.org/wiki/List_of_epidemics)
- [Prime Ministers of Canada](http://www.downloadexcelfiles.com/ca_en/download-excel-file-list-prime-ministers-canada)
- [Presidents of France](http://www.downloadexcelfiles.com/fr_en/download-excel-file-list-presidents-france)
- [Chancellors of Germany](https://en.wikipedia.org/wiki/List_of_Chancellors_of_Germany)
- [Presidents of Italy](http://www.downloadexcelfiles.com/it_en/download-excel-file-list-presidents-italy)
- [Prime Ministers of Japan](http://www.downloadexcelfiles.com/jp_en/download-excel-file-list-prime-ministers-japan)
- [Prime Ministers of the UK](http://www.downloadexcelfiles.com/gb_en/download-excel-file-list-prime-ministers-uk)
- [Presidents of the USA](https://raw.githubusercontent.com/hitch17/sample-data/master/presidents.json)
- [C4-5 Hurricanes: 1960-2010](http://www.aoml.noaa.gov/hrd/hurdat/easyread-2011.html)
- [The Daily Routines of Famous Creative People](https://podio.com/site/creative-routines)
-['Visualizing painters' lives" by Accurat](http://www.brainpickings.org/2013/06/07/painters-lives-accurat-giorgia-lupi/)
- ['From first published to masterpieces' by Accurat](http://www.brainpickings.org/2013/11/29/accurat-modern-library/)
- [Kurzweil's 'Countdown to Singularity'](http://www.singularity.com/images/charts/CountdowntoSingularityLog.jpg)
- ['A Perspective on Time' by mayra.artes for Wait But Why](http://visual.ly/perspective-time)
- ['Life of a Typical American' by Tim Urban for Wait But Why](http://waitbutwhy.com/2014/05/life-weeks.html)

## OSS Libraries / scripts used in this project

- [d3 v3.5.5](http://d3js.org/) for visual encoding, scales, animation
- [d3-time v0.0.2](https://github.com/d3/d3-time) for date parsing / temporal arithmetic
- [moment.js v2.10.6](http://momentjs.com/) for date parsing / temporal arithmetic
- [saveSvgAsPng.js](https://github.com/exupero/saveSvgAsPng) for image export
- [intro.js 2.3.0](http://usablica.github.com/intro.js/) for tour
- [gif.js](https://github.com/jnordberg/gif.js) for GIF exporting
- [gsheets 2.0.0](https://github.com/interactivethings/gsheets) for Google Spreadsheet import
- [nodejs](https://nodejs.org/)
- [express](https://www.npmjs.com/package/express)
- [socket.io](https://www.npmjs.com/package/socket.io)

## Noun Project icons used in the user interface

All Icons [CC BY 3.0](https://creativecommons.org/licenses/by/3.0/us/), by name and author:

- [check-mark](https://thenounproject.com/term/check-mark/608852) (Arthur Shlain)
- [calendar](https://thenounproject.com/term/calendar/38869) (Kiril) Tomilov)
- [timeline](https://thenounproject.com/term/timeline/152347) (Alecander) Bickov)
- [gif-file](https://thenounproject.com/term/gif-file/446903) (Pranav Grover)
- [png-file](https://thenounproject.com/term/png-file/446907) (Pranav Grover)
- [svg-file](https://thenounproject.com/term/svg-file/446904) (Pranav Grover)
- [json-file](https://thenounproject.com/term/json-file/446959) (Pranav Grover)
- [csv-file](https://thenounproject.com/term/csv-file/446962) (Pranav Grover)
- [drive](https://thenounproject.com/term/drive/128372) (Denis Klyuchnikov)
- [grid](https://thenounproject.com/term/grid/539919) (Doejo)
- [folder](https://thenounproject.com/term/folder/43216) (iconoci)
- [filter](https://thenounproject.com/term/filter/132317) (Creative) Shell)
- [image](https://thenounproject.com/term/image/332296) (Creative) Shell)
- [quotation-mark](https://thenounproject.com/term/quotation-mark/378366) (Veronika Krpciarova)
- [pin](https://thenounproject.com/term/pin/172903) (Alexandr Cherkinsky)
- [eraser](https://thenounproject.com/term/eraser/3715) (Terrence Kevin Oleary)
- [invisible](https://thenounproject.com/term/invisible/506290) (Kid A)
- [book](https://thenounproject.com/term/book/861149) (Setyo Ari Wibowo)
