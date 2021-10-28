# aws_cm
## SS

<details><summary><b>1.auto_scale_max_count.py:</b></summary>
<br>

**Intension of script:**

Updating maximum_capacity based on user_maximum_capacity.

**Work flow:**
* 	Getting max scale count from user_max_capacity (auto scaling maximum capacity).
* Have to get data from database (ss. auto_scaling_groups) where maximum_capacity! = user_maximum_capacity. 
* 	If dataframe is empty, then scripts will stop as there is no work.
* 	If data frame is not empty, then Converting columns data in list format and to get same row data to do further operation.
* 	Calling max_count_update () to update max capacity based on user_maximum_capacity in aws console.
* 	In max_count_update we have to create client by passing account_id, region, assume_role, service name i.e. 'auto scaling'.


</details>
<!-- ########################################################################### -->
<details><summary><b>2.auto_scaling.py</b></summary>
<br>

**Intension of script::**

Getting autos calling group details from aws console and store it in database.


**Work flow:**
* Getting account details from ad.aws_accounts.
* Getting columns from "ss.auto_scaling_groups".
* Creating an empty dataframe(data_from_aws) with table column name to store data from aws.
* Account wise (in account id list): Here getting details of that particular account like (region , assume role, account name )--> region wise(in region list ): Here creating clients(like "autoscaling","ec2","ssm") acc. requirement .
* Using created client call required methods(auto_client.describe_policies(),auto_client.describe_tags(),auto_client.describe_auto_scaling_groups ()) to get data from aws console and convert it into json data.
* From json data get required data to store data in database.
* Note: In auto scaling we can’t get all required data from one method. Here we are using 3 different methods i.e. auto_client. describe_policies(),policy deatils, auto_client.describe_tags(),for tags deatils ,auto_client.describe_auto_scaling_groups (), for    getting details of auto scaling group.
* After getting required data append all required data in data frame.
* If data frame is empty it will go for remove_records () and clear all previous data as nothing to store in data base.
* If data frame is not empty it will go for pass_to_db() and do curd operations with condition.


</details>



<!-- ########################################################################### -->


<details><summary><b>3.ec2.py:</b></summary>
<br>

**Intension of script::**

Getting ec2 instances details from aws console and store it in database.

**Work flow:**
*	Getting account details from ad.aws_accounts.
*	Getting columns from "ss.ec2_instances_schedules".
*	Creating an empty data frame(data_from_aws) with table column name to store data from aws.
*	Account wise (in account id list): Here getting details of that particular account like (region , assume role, account name )-->region wise(in region list ): Here creating clients(like "ec2","ssm","pricing") acc. requirement .
*	Using created client call required methods(ec2.describe_instances()) to get data from aws console and convert it into json data.
*	From json data get required data to store data in database.
*	After getting required data append all required data in data frame.
*	If data frame is empty it will go for remove_records () and clear all previous data as nothing to store in data base.
*	If data frame is not empty it will go for pass_to_db() and do curd operations with condition.


![alt text](https://viewer.diagrams.net/?tags=%7B%7D&highlight=0000ff&edit=_blank&layers=1&nav=1#R7VpdU9s4FP01eYSxLTsJjwQC7UzLdiaz2%2FLECPsm0a5suZJMEn79SpYcfwYMhDRMCzNgXX1Z95x777GTAbqI19ccp8uvLAI68JxoPUCXA88bjT31Vxs2xuAPx8aw4CQyJrc0zMgjWKNjrRmJQNQGSsaoJGndGLIkgVDWbJhztqoPmzNa3zXFC2gZZiGmbet3EsmlsY4Dp7R%2FArJYFju7ju2JcTHYGsQSR2xVMaHpAF1wxqS5itcXQLXvCr%2BYeVc7erc3xiGRfSZ8TlxfzuLZ493N98k3chY%2B%2FnN5YtF5wDSzB55JzKW9Y7kp3MBZlkSgV3IHaLJaEgmzFIe6d6VwV7aljKntnhNKLxhlPJ%2BLwI0CGCm7kJz9B5Wes%2BEI4aHqaZ%2FFHu8BuIR1xWTPdg0sBsk3aojtRWPrZ0u0AqFVidoWm2UFMd%2FasCXKYrty6Ut1Yd35AteilmunN5cf0bGjumN91OFZr8Ozw%2FfyrOu2XNvyK0QqjG2TcblkC5ZgOi2tk9LzjmqVY74wllp%2F%2FwtSbmxOwplkDTRYIq9wTKh2zCegDyBJiG2HneW6T4EgWMZDeOKkvs14mC9APjEuMOP0oZ%2BElAPFkjzUc9ve8fE74BlSdf%2BTVGdqioXZcfgz08lv8lWwG8ZjTEuTvi1KFkltXKj8B7w2qES8MGrnn4jc%2B%2BdqgIvSdXXGcGH%2F5%2FcjUpyoQRQni9oi05uTv2fPbERJAicF3%2FOtnNHAC9qbXSsWEbWB3fOeFx04DBUHpa6OIDGhQhcozmJ9%2BOgUr8RdBNh2mLkKDnPL9WMoc1ra9phh5oH%2BtV6t2M1PV%2BYZ5j%2F7yTzeKKhlnm2WqWQe5B4y8wQHY%2FYBeOqYGc2AcbsCZsthJ1KMrFL5qhhSMHcljBwTTN2ITjkLwpIcNKHbVKVXs1JJf%2BVz1Uyi%2FP4ZN90k70m2W6rQwDGcHi4U%2BqR3dGwxg7x6td4K6UrMeIet1v6vKM6wJvJH5fpWL3Ua2Nbl2q6cNzZFI1Hn%2FVFtVGbpZjktbxXzDiAEhj2FwPiohIAb%2FEroS7hvKz3PQV%2BifVsD%2B%2BihR8cF%2Feh30eh98RkdFT7DY1cyZtrneaP%2B63NpgQFxKjdv0gJLFt9nYk864CntvLve71II%2B9ABjdchyOn5PmT8XjqgKyG8mHFvItMEC9AaU8vRDgFb6tHEEI1DzB7AIKEwzyjmuSQVEichVImZK18hnhOnb5HxTZnunzqp3Ir4XiJ%2Fblms%2B9XCOE7zToR8HbgqzxEduU4Cq1ZvFwbOjtNC6N0VThJ3IlxClFEQ2zWTe5G%2BHsTj0v8dcR9hGM%2FDzrgPx3A%2F3098u6hHfI864nv0XvE9%2FhgVpZoEnFbIZ6mKaX3BbKgDl2Wgk%2B7EoUTHy4PB%2BcP%2Ft%2FA%2FGNffDaGO51w3CA74nHvWQ%2FAm0bn%2BTEq18nggYd3ldbnbG4BDPvC8Xid7PXWy31MnV4AOOvJcYestp%2B0O3xjJE4Llmd%2FIs67b4I85t51V%2FfituZDTeJl51ljIOKa1UM7F7bHf8EDmfSh%2Bvp5nQU%2BeDY%2BLZ27jvV2THr151iBsq%2BDv4JkCHm8qw1I9QPQPjEKAlLQ1K%2B6XxG2RcTudtXisaoisM7eQFVZMoImuNIqt9Nx2xCSKzCsHUCIb3%2BdLaSJaP6h1g8kguNRrZZIJS%2B9WmUtYAo2aWJiaZXNX%2BOyhOqImOB3V0e8gs%2FdexdFtV8ebv%2F7g1sTNP3te1aD94Kaa5XdPTHyWX%2BBB0%2F8B)

</details>


<!-- ########################################################################### -->

<details><summary><b>4.ec2_autostop.py:</b></summary>
<br>


</details>




<!-- ########################################################################### -->

<details><summary><b>5.ec2_scheduled_start.py:</b></summary>
<br>

**Intension of script::**

It has to start instances based on start time stored in database.

**Work flow:**
*	Have to get data from database (ss. ec2_instances_schedules) where sys_time=str_time and store in data_from_database data frame. 
*	If data_from_database is empty it terminate as there is no instance ready to start.
*	Otherwise it will follow following steps.
*	Convert column data into list format.
*	Pass values data_from_database, connection, i (particular index value) to start_ec2().
*	In start_ec2 function it will create ec2 client and will pass accound_id, region, assume role of that particular instance then it will call start_instances () method to start instance.



</details>



<!-- ########################################################################### -->

<details><summary><b>6.ec2_scheduled_stop.py:</b></summary>
<br>

**Intension of script::**

It has to start instances based on stop time stored in database.

**Work flow:**
*	Have to get data from database (ss. ec2_instances_schedules) where sys_time=stp_time and store in data_from_database data frame. 
*	If data_from_database is empty it terminate as there is no instance ready to stop.
*	Otherwise it will follow following steps.
*	Convert column data into list format.
*	Pass values data_from_database, connection, i (particular index value) to stop_ec2().
*	In stop_ec2 function it will create ec2 client and will pass accound_id, region, assume role of that particular instance then it will call stop_instances () method to start instance.



</details>


<!-- ########################################################################### -->



<details><summary><b>7.rds.py:</b></summary>
<br>

**Intension of script::**

Getting rds database details from aws console and store it in database.

**Work flow:**
*	Getting account details from ad.aws_accounts.
*	Getting columns from "ss. rds_databases_schedules".
*	Creating an empty data frame(data_from_aws) with table column name to store data from aws.
*	Account wise (in account id list): Here getting details of that particular account like (region , assume role, account name )--> region wise(in region list ): Here creating clients(like "rds","ssm","pricing") acc. requirement .
*	Using created client call required methods(rds. describe_db_instances ()) to get data from aws console and convert it into json data.
*	From json data get required data to store data in database.
*	After getting required data append all required data in data frame.
*	If data frame is empty it will go for remove_records () and clear all previous data as nothing to store in data base.
*	If data frame is not empty it will go for pass_to_db() and do curd operations with condition(based on account name).


</details>

<!-- ########################################################################### -->


<details><summary><b>8.rds_autostop.py:</b></summary>
<br>
</details>

<!-- ########################################################################### -->



<details><summary><b>9.rds_scheduled_start.py:</b></summary>
<br>

**Intension of script::**

It has to start rds database based on start time stored in database.

**Work flow:**
*	Have to get data from database (ss. rds_databases_schedules) where sys_time=str_time and store in data_from_database data frame. 
*	If data_from_database is empty it terminate as there is no database ready to start.
*	Otherwise it will follow following steps.
*	Convert column data into list format.
*	Pass values data_from_database, connection, i (particular index value) to start_db().
*	In start_rds function it will create rds client and will pass accound_id, region, assume role of that particular database then it will call start_db () method to start database.


</details>
<!-- ########################################################################### -->
<details><summary><b>10.rds_scheduled_stop.py:</b></summary>
<br>

**Intension of script::**

It has to start rds database based on stop time stored in database.

**Work flow:**
*	Have to get data from database (ss. rds_databases_schedules) where sys_time=stp_time and store in data_from_database data frame. 
*	If data_from_database is empty it terminate as there is no database ready to stop.
*	Otherwise it will follow following steps.
*	Convert column data into list format.
*	Pass values data_from_database, connection, i (particular index value) to stop_db().
*	In start_db function it will create rds client and will pass accound_id, region, assume role of that particular database then it will call stop_db () method to start database.
</details>
<!-- ########################################################################### -->
<details><summary><b>11.scheduled_scale_in.py:</b></summary>
<br>

**Intension of script:**

Updating scale_in_count minimum capacity at scale_in_time.

**Work flow:**

* Have to get data from database (ss. auto_scaling_groups) where sys_time = scale_in_time. 
* If dataframe is empty, then scripts will stop as there is no work.
* If data frame is not empty, then Converting columns data in list format and to get same row data to do further operation.
* Calling scale_in () to update minimum capacity based on scale_in_count in aws console.
* In scale_in we have to create client by passing account_id, region, assume_role, service name i.e. 'auto scaling'.
* It will upadte minimum capacity with scale_in_count at mentioned time database.

</details>
<!-- ########################################################################### -->
<details><summary><b>12.scheduled_scale_out.py:</b></summary>
<br>

**Intension of script:**

Updating scale_out_count with minimum capacity at scale_out_time.

**Work flow:**

* Have to get data from database (ss. auto_scaling_groups) where sys_time = scale_out_time. 
* If dataframe is empty, then scripts will stop as there is no work.
* If data frame is not empty, then Converting columns data in list format and to get same row data to do further operation.
* Calling scale_out () to update minimum capacity based on scale_in_count in aws console.
* In scale_in we have to create client by passing account_id, region, assume_role, service name i.e. 'auto scaling'.
* It will upadte minimum capacity with scale_out_count at mentioned time database.
</details>
