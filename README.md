# Data Generator Utility Project
The Data Generation Utility is a command-line tool designed to aid in testing data pipelines by generating customizable JSON test data. Whether you're validating data transformations, testing data validations, or simply need mock data for development purposes, this utility simplifies the process.
## Features
<li><b>Flexible Configuration</b>: Customize file count, file name prefix, data schema, and more through command-line arguments or a configuration file.</li>
<li><b>Multiple Prefix Options</b>: Generate files with sequential counts, random prefixes, or UUID prefixes for easy organization.</li>
<li><b>Supports Multiprocessing</b>: Utilize multiple CPU cores to generate data files efficiently, speeding up the process for larger datasets.</li>
<li><b>Schema Validation</b>: Validate data schema correctness to ensure generated data adheres to specified rules.</li>

## How to use
<li>Fork or Clone the repository</li>
<li>Run the utility with desired command-line arguemnts or customize configurations in 'default.ini'.</li>
<li>Generated JSON files will be saved to the specified directory.

## List of input params for CU:

<table>
  <tr>
    <th>Name</th>
    <th>Description</th>
    <th>Behaviour</th>
  </tr>
  <tr>
    <td>path_to_save_files</td>
    <td>Where all files need to save</td>
    <td>2 ways to define path:
        Relatively from cwd and absolute <br>
        '.' - means current path (default)</td>
  </tr>
  <tr>
    <td>files_count</td>
    <td>How much json files to generate</td>
    <td>Default: 4</td>
  </tr>
  <tr>
    <td>file_name</td>
    <td>Base file_name</td>
    <td>If there is no prefix, the file name will be file_name.json <br>
        With prefix full file name will be file_name_file_prefix.json</td>
  </tr>
  <tr>
  <td>file_prefix</td>
  <td>Prefix name for file if more than 1 file needs to be generated</td>
  <td>Possible choices:<br>
    <li>count</li>
    <li>random</li>
    <li>uuid</li></td>
  </tr>
  <tr>
  <td>data_schema</td>
  <td>String with json schema</td>
  <td>It can be loaded in two ways:
    <li>With path to json file with schema</li>
    With schema entered to command line<br>
  </tr>
  <tr>
  <td>data_lines</td>
  <td>Count of lines for each file</td>
  <td>Default: 100</td>
  </tr>
  <tr>
  <td>multiprocessing</td>
  <td>The number of processes used to create files</td>
  <td>Default: 1</td>
  </tr>
</table>

## Example usage

<li>Example of data schema:<br>
<code>{"date":"timestamp:", "name": "str:rand", "type": "str:['client', 'partner', 'government']", "age": "int:rand(1, 90)"}</code></li>

<li>Simple usage with default values:<br>
<code>cli.py</code></li>

<li>Usage with data schema from file:<br>
<code>cli.py --file_count=3 --file_name=super_data --prefix=count --data_schema=./path/to/schema.json</code></li>

<li>Usage with provided data_schema from cmd:
<code>cli.py --file_count=3 --file_name=super_data --prefix=count --multiprocessing=4 --data_schema="{\"date\": \"timestamp:\", \"name\": \"str:rand\", \"type\" : \"['client', 'partner', 'government']\", \"age\":\"int:rand(1, 90)\"}"</code>

## TODO in future:
<li>Add testing</li>
<li>Add clear_path flag</li>
