
# CC-Research-tutorial3

Starting steps- creating the database in S3

![image](https://github.com/eliya18/CC-Research-tutorial3/assets/49730658/9097a2ff-fe76-4283-8da2-5efa22d3bba0)

Then copy the URI into amazon glue

![image](https://github.com/eliya18/CC-Research-tutorial3/assets/49730658/d59c6e20-1dd9-4df1-9ecc-db692df7523a)

After following all steps to create the crawler, it was created successfully

![image](https://github.com/eliya18/CC-Research-tutorial3/assets/49730658/f90d1f4d-890d-404d-98ba-bdf2b9babe9c)

Then running the crawler

![image](https://github.com/eliya18/CC-Research-tutorial3/assets/49730658/03e7efa8-d574-4ee4-82c1-035f87eabc0f)

And the new table has been created in amazon glue

![image](https://github.com/eliya18/CC-Research-tutorial3/assets/49730658/dcb81804-2097-458a-b180-e5963f8f50b6)

The data source in the ETL visual was created with the proper details

![image](https://github.com/eliya18/CC-Research-tutorial3/assets/49730658/85d51995-ab40-4cda-88f2-1aa7d739c6d3)

Adding the target to the ETL process

![image](https://github.com/eliya18/CC-Research-tutorial3/assets/49730658/7a21f489-56e2-496d-b662-ba7a0541970e)

Running the job

![image](https://github.com/eliya18/CC-Research-tutorial3/assets/49730658/edc62009-cb0b-4712-9e87-db1116fdad83)

After 1 minute and 6 second the job was completed successfully

![image](https://github.com/eliya18/CC-Research-tutorial3/assets/49730658/08dc1e8d-69fc-4828-94d3-2984128b48f8)

Data are indeed exist in the target folder sets

![image](https://github.com/eliya18/CC-Research-tutorial3/assets/49730658/92f39f84-0c74-4b37-9e25-e92a7715a048)

Trigger creation and that it's indeed active and scheduled

![image](https://github.com/eliya18/CC-Research-tutorial3/assets/49730658/7b53e293-f0ee-464a-8d53-1b64ce39ab49)

![image](https://github.com/eliya18/CC-Research-tutorial3/assets/49730658/2d61bb80-e6e0-46fe-bfee-d5615834181d)

To sum up, the tutorial is a striaght forward guide to demonstrate how to create an E2E ETL process which indcludes creation of a data source and target for the results of the ETL.
In addition, it shows it's application so the data can be seen in the target folder of the example ETL process.
It is helpfull and easy to understand how to do-it-youself in case a developer wants to add transformations (e.g. filters, join, etc.) to the data. 
