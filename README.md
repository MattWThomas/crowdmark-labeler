# Crowdmark Labeler

This is a Python function which automatically labels exams outputted by Crowdmark using the names of students provided in a `pandas` dataframe. This script depends on `pdfrw`, `reportlab`, and `pandas`. This is designed for assessments which have the "Enable automated matching" option enabled when booklets are generated in Crowdmark. The script will fill the name box that looks like this:

![before labeling](https://raw.githubusercontent.com/MattWThomas/crowdmark-labeler/master/assets/before.png)

to make it look like this

![after labeling](https://raw.githubusercontent.com/MattWThomas/crowdmark-labeler/master/assets/after.png)

## Enviroment
You can install the dependences with:
```
pip install pandas pdfrw reportlab
```

## Function

The main Python script, [`clabeler.py`](clabeler.py) defines the function `labelbooklets` defined in the following way:
```python
def labelbooklets(labels, pagecount, booklets="booklets.pdf", output="labeled_booklets.pdf", colfname="fname", collname="lname", colid="netID"):
```
the function takes the arguments

* **labels:** A pandas dataframe containing the student names and netIDs
* **pagecount:** The number of pages in each exam
* **booklets:** The path to the exam booklets generated by Crowdmark; defaults to "booklets.pdf" in the working directory
* **output:** The path to output the labeled booklets; defaults to "labeled_booklets.pdf" in the working directory
* **colfname:** The name of your student first name column in your labels dataframe; defaults to "fname"
* **collname:** The name of your student last name column in your labels dataframe; defaults to "lname"
* **colid:** The name of your student ID column in your labels dataframe; defaults to "netID"

## Example
An example is provided in the example folder. It contains:

* an excel spreadsheet of fake names called [`labels.xlsx`](example/labels.xlsx) and an identical tab delimited file called [`labels.txt`](example/labels.txt)
* a fake exam with a Crowdmark name box called [`booklets.pdf`](example/booklets.pdf)
* a script that calls the `labelbooklets ` function called [`example.py`](example/example.py)

The output of this example is the included [`labeled_booklets.pdf`](example/labeled_booklets.pdf)

## License

Crowdmark Labeler is licensed under the [MIT License](LICENSE).

## FAQ

Why does the inserted text look different/bad on my device?
> The script uses the font "Courier" when inserting text. While all versions of Acrobat reader, Windows, and Mac OSX have this font, not all readers and systems do (eg. Android). This is not a limitation unless you intend to print with a device that does not support this font.

Does this support documents with A4, legal, etc. paper?
> No, it only supports letter paper at the moment. It should be easy to add other formats. Please create an issue (or pull request) if you would like to see any other paper size supported.

Can I install this function using pip?
> No, this is just a script. It is not currently a Python package.
