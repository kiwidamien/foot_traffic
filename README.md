# foot_traffic


An analysis of where to put a new store!

## Install / running

It is recommended that you review the main notebook in either JupyerLab, or using the [collapable headings](https://jupyter-contrib-nbextensions.readthedocs.io/en/latest/nbextensions/collapsible_headings/readme.html) extention for Jupyter notebook. The EDA is quite long, and collapsing the sections will help navigate around the file faster.

I have introduced _pinned_ versions of the requirements. Other than the category encoder package, most of the packages used here should be in the standard data science toolkit. To duplicate my environment, run

```bash
# Do this in a virtual env! The pinned versions might alter dependencies on
# other projects you are working on
$ pip install -r requirements.txt
```


## Layout

```
.
├── Data\ Scientist\ Evaluation\ Test.docx
├── README.md
├── data
│   ├── train.csv
│   └── validation.csv
├── install_kernel.sh
├── location_analysis.ipynb
├── requirements.txt
└── summary.ipynb
```

The files that are of most interest are 
- [location_analysis](./location_analysis.ipynb), which is the detailed EDA and modeling I did
- [summary](./summary.ipynb), which contains a high-level summary of the modeling work, results, and further work that could be done.


## Data Dictionary

| Feature name    | Meaning                         |  Type          |
| --------------- | ------------------------------- | -------------- |
| directionCode   | Encoding of directoin (1,2,3,4) | Categorical    |
| `r_*`           | Proprietary features            | Floats (quant) |
| totalActivitiesRefcircle | Sample activities      | Int (quant)    |
| totalCustomersRefcircle | Sample customers        | Int (quant)    |
| dayname         | Day of Week name (Mon, Tue, etc) | Categorical   |
| date            | Date of measurement             | Date           |
| weekend         | Flag for weekend (yes/no)       | Categorical    |
| isholiday       | is a holiday (yes/no)           | Categorical    |
| transCount      | Number of transactions          | Int (quant)    |
| totalRevenue    | Total Revenue                   | Float (quant)  |
| Seats           | Number of seats                 | Int (quant)    |
| Parking_slots   | Number of parking slots/spaces  | Int (quant)    |
| type_dfsf       | Type of store                   | Categorical    |
| mtype           | Market type                     | Categorical    |

We can tell that the date column holds all of the information for th  dayname and weekend column (`isholiday` is a little
more complicated to extract). We are also able to see (in the analysis) that we have 25 identical stores in the training
set, where a store has unique values of 

- directionCode
- Seats
- Parking_slots
- type_dfsf
- mtype


While we have a lot more rows than 25 in training, the data we have comes from sampling these stores on different dates.
