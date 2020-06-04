
<h1>Invoice status checker.</h1> 

<h3> Windows version. </h3>

<b>Brief description:</b>

This python script operates on CSV and spreadsheet xlsx files. The main function of this script is to retrieve specified data from the given query data files and return relevant information.

Technology and libraries used:
<ul>
<li> python 3 </li>
<li> pandas </li>
<li> openpyxl </li>
<li> glob </li>
<li> os </li>
</ul>

<h3> Who is this for? </h3>

The main purpose of the script is to automate manual, inefficient manipulation in one of the working processes in a company where I work. Although it serves only mine and my colleague's needs, anyone who works with data, CSV, and Excel spreadsheets may find some parts of the code relevant for their purposes.


<b>Disclaimer:</b> 

I am a beginner Python user and this is my first working project that does something useful. I understand that the code might be far from perfect, however, it does its job. Anyway, I will appreciate any comments or suggestions on how to make it better.

<h3> Full description: </h3>

Every day during the work process in the company where I work we have to respond to mail requests and provide updated statuses of the invoices that are registered in our database. The list might include a huge number of the invoices we need to check (up to 100-150 pc.) Before this tool was created, we could retrieve only one invoice at a time in two databases that we use. The way we operated while providing statuses of invoices required only manual copy-paste steps that took a lot of time and was super boring and inefficient. So that how I come up with the idea to create this tool.

As I mentioned before, we use two databases: one is for the invoices that are not processed, and another is for the processed ones (Oracle database). Although both databases use SQL, unfortunately due to corporate  burocracy obtaining direct access to the databases could last for years. The databases use GUI that allows us to make queries and download required data as CSV or Excel files. After making a query, we get 3 different data files (2 CSV and XLSX) that contain data of hundreds or thousands of invoices.
<p>

The first CSV file contains data about processed pre-processed invoices. 
The second CSV contains information about approvers of invoices. The last one hold payment schedule date and actual payment date.

There could be more than 10 possible statuses for an invoice:

STATUS_CODES = 

{'R1': 'Returned', <br>
'C1': 'Cancelled', <br>
'20': 'Unprocessed E-invoice', <br>
'4': 'Cancelled Invoices', <br>
'3': 'Transferred to GFIS', <br>
'2': 'Ready to transfer', <br>
'1': 'Sent for approval', <br>
'0': 'Unprocessed'}	<br>						

Missing <br>

Scheduled due [date], paid on [date] <br>

or <br>

Scheduled due [date], Not paid <br>

<h4> How it works? </h4>

First, we need to create "check_invoices.xlsx" file where we place the list of the invoices  whose updated statuses are required. The tool loads the list and seeks for each of the position (invoice number) in downloaded data query files. If the invoice number is recorded in any of the given data files, its actual status will be copied and transferred to the "check_invoices.xlsx" file. If the invoice was not found, the status will be updated as "Missing".










