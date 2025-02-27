# Create and Associate Disaster Recovery Protection Groups

## Introduction

In this lab, we will Create and Associate Disaster Recovery Protection Groups (DRPG). Ashburn is a primary region, and Phoenix is the standby region.

What is DRPG – A resource type used by FSDR.  A DR Protection Group represents a consistency grouping defined for the purposes of disaster recovery.  It is a collection of different OCI resources that comprise an application and must be treated as a combined group when performing disaster recovery operations.  For example, a DR Protection Group may consist of application servers (compute instances), associated block storage (grouped as volume groups), and databases.

Estimated Time: 5 Minutes

Watch the video below for a quick walk through of the lab.

[Create and Associate DRPG](videohub:1_e046v6gz)

### Objectives

- Create DRPG in Ashburn and Phoenix regions.
- Associate Ashburn DRPG as primary and Phoenix DRPG as Standby

## Task 1: Create DRPG in Ashburn and Phoenix regions

1. Login into OCI Console with your provided Credentials. The primary region should be **Ashburn**.

  ![Ashburn OCI Console](./images/ashburn-region.png)

  Open another browser tab and then select region as **Phoenix** (Standby Region)

  ![Phoenix OCI Console](./images/phoenix-region.png)

2. In the first browser tab,Select **Migration and Disaster Recovery** from the Hamburger menu, then **Disaster Recovery** -> **DR Protection Groups**. Verify the region in **Ashburn**

  ![DRPG from ashburn](./images/ashburn-drpgpage.png)

3. In the second browser tab,Select **Migration and Disaster Recovery** from the Hamburger menu, then **Disaster Recovery** -> **DR Protection Groups** Verify the region in **Phoenix**

  ![DRPG from phoenix](./images/phoenix-drpgpage.png)

4. You will land up at the Disaster Recovery Protection group home page; make sure to have two tabs opened for Ashburn and Phoenix region.

  ![DRPG landing page](./images/ashburn-drpg.png)
  ![DRPG landing page](./images/phoenix-drpg.png)

5. Create DRPG in the Ashburn region. Select Create DR Protection group in the Ashburn region browser tab and follow the below instructions.

- Enter name as **mushop-ashburn**
- Select the compartment assigned to you
- In the object storage bucket, use the drop-down option and select **mushop-xxxxx** (mushop-12345)  ( Don't select mushop-media-xxxxx bucket)
- In role, leave it as **Not Configured**
- Ignore add member
- Verify and hit create

  ![create drpg](./images/ashburn-drpgcreate.png)

Navigate back to the DR Protection group page; the state of DRPG will change from creating to active in a few seconds.

  ![drpg status](./images/ashburn-drpgactive.png)

6. Create DRPG in the Phoenix region. Select Create DR Protection group in the Phoenix region browser tab and follow the below instructions.

- Enter name as **mushop-phoenix**
- Select the compartment assigned to you
- In the object storage bucket, use the drop-down option and select **mushop-xxxxx** (mushop-12345) ( Don't select mushop-media-xxxxx bucket)
- In role, leave it as **Not Configured**
- Ignore add member
- Verify and hit create

  ![create drpg](./images/phoenix-drpgcreate.png)

Navigate back to the DR Protection group page; the state of DRPG will change from creating to active in a few seconds.

  ![drpg status](./images/phoenix-drpgactive.png)

## Task 2: Associate Ashburn DRPG as primary and Phoenix DRPG as Standby

1. From the Ashburn region OCI console, select **mushop-Ashburn** DRPG. Select the **Associate** button

  ![drpg associate](./images/drpg-associate.png)

- Select Role as **Primary**
- Select Peer Region as **US West (Phoenix)**,
- Select Peer DR Protection group in the compartment (change assigned compartment if required); you should select **mushop-phoenix**
- Verify and associate

  ![drpg associate confirm](./images/drpg-associate-1.png)

  **mushop-ashburn** DRPG will change to *Updating* State

  ![drpg associate update](./images/drpg-associate-updating.png)

  Navigate back to the DR Protection group home page. You should be able to see DRPG **mushop-ashburn** state as *Active*, role as *Primary*, peer region as *US West (Phoenix)*

  ![drpg associate done](./images/drpg-status-ashburn.png)

2.From the Phoenix region OCI console, navigate to the DR Protection group home page. You should be able to see DRPG **mushop-phoenix** state as *Active*, role as *Standby*, peer region as *US East (Ashburn)*

   ![drpg associate status](./images/drpg-status-phoenix.png)

   Now, we have associated **mushop-Ashburn** as *Primary DRPG* and **mushop-phoenix**  as *Standby DRPG*

   You may now **proceed to the next lab**.

## Acknowledgements

- **Author** -  Suraj Ramesh, Principal Product Manager
- **Last Updated By/Date** -  Suraj Ramesh,September 2022
