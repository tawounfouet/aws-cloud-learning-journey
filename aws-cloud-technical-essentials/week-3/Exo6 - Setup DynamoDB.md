# Exercise 6: Setting up the Database
In this scenario, part of your responsibility is to keep the employee database up to date.

In this exercise, you first launch another EC2 instance. Then, you create the DynamoDB table for the employee directory application.

Task 1: Launching an EC2 instance
In this task, you will launch another EC2 instance.

If needed, log in to the AWS Management Console as your Admin user.

Open the Amazon EC2 console by searching for and choosing EC2.

In the navigation pane, choose Instances.

If needed, select the check box for the employee-directory-app-s3 instance, which should be in the Stopped state.

Choose Actions and then choose Image and templates, Launch more like this.

For Name and at the end of the Value, append -exercise6.

Example:

   employee-directory-app-exercise6
Copy to clipboard
For Key pair name, select app-key-pair.

Under Network settings and Auto-assign Public IP, choose Enable.

Choose Launch instance.

Choose View all instances.

The instance should now be in the Instances list.

Wait for the Instance state to change to Running and the Status check to change to 2/2 checks passed.

If needed, clear the check box for the employee-directory-app-s3 instance.

Select the check box for employee-directory-app-exercise6.

Copy the Public IPv4 address.

Note: Make sure that you only copy the address instead of choosing the open address link.

In a new browser window, paste the IP address that you copied. Make sure to remove the ‘S’ after HTTP so you are using only HTTP instead.

You should see an Employee Directory placeholder. You won’t be able to interact with the application yet because it’s not connected to a database.

Close the application browser window.
Task 2: Creating the DynamoDB table
To connect the application to a database, you first need to create one! In this task, you will create a database by using DynamoDB.

Return to the console, and search for and open DynamoDB.

In the navigation pane, choose Tables.

Choose Create table and configure the following settings.
Table name: Employees
Partition key: id
Choose Create table.

Task 3: Testing the application
In this task, you will test whether the application works by using it to create an employee entry and upload a photo.

Return to the Amazon EC2 console by searching for and opening EC2.

In the instance list, select the check box for the employee-directory-app-exercise6 instance.

On the Details tab, copy the Public IPv4 address and in a new browser window, paste the IP address.

In the application interface, choose Add.

Create a new employee entry by entering a name, location, and job title, and by selecting some attributes.

Upload a picture by choosing Browse and uploading a picture of your choice.

Choose Save.

Create and save a few employee entries.

Note: You can also edit and delete entries.

In the employee directory application, you should now see the list of employees (and their photos) that you added.

Task 4: Viewing the item in the database
In this task, you will see how the employee entries are stored in DynamoDB.

Return to the console, and search for and open DynamoDB.

In the navigation pane, choose Tables.

Open the table details by choosing the Employees link.

Choose Explore table items.

In the Items returned list, you should now see the entries in the database that you made by using the application on the EC2 instance.

Congratulations! You launched an EC2 instance that uses the S3 bucket, and is connected to the DynamoDB table.

Task 5: Stopping your EC2 instance
In this task, you will now stop the instance to prevent future costs from incurring.

Note: Do not terminate the instance because you will use it in the next exercise.

Return to the Amazon EC2 console by searching for and opening EC2.

If needed, in the navigation pane, choose Instances.

Select the check box for employee-directory-app-exercise6.

Choose Instance state and then choose Stop instance.

In the dialog box, choose Stop.

The Instance state will eventually go into the Stopped state.

