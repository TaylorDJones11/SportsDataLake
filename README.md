# SportsDataLake - Day 3

# **NBA Data Lake Setup Guide**

## **Step 1: Open AWS CloudShell**
1. Go to [aws.amazon.com](https://aws.amazon.com) and sign in to your AWS account.  
2. In the AWS console, locate the CloudShell icon (a square with `>_` inside) next to the search bar and click it to open the CloudShell environment.

---

## **Step 2: Create and Configure the `setup_nba_data_lake.py` Script**
1. In the CloudShell terminal, create a new Python script by typing:
   ```bash
   nano setup_nba_data_lake.py
   ```

2. Open another window and navigate to GitHub
3. Copy the contents of the nba_data_lake.py file from the repository.
4. Return to the CloudShell window and paste the copied contents into the file.
5. Locate the Sportsdata.io API configuration section in the script:
   ```bash
   api_key = "your_api_key_here"
   ```
6. Save and exit:
- Press Ctrl + X to exit
- Press Y to confirm saving the file
- Press Enter to confirm the filename.

## **Step 3: Create .env file**
1. In the CLI (Command Line Interface), type
```bash
nano .env
```
2. paste the following line of code into your file, ensure you swap out with your API key
```bash
SPORTS_DATA_API_KEY=your_sportsdata_api_key
NBA_ENDPOINT=https://api.sportsdata.io/v3/nba/scores/json/Players
```

3. Press ^X to exit, press Y to save the file, press enter to confirm the file name

## **Step 4: Run the Script**
Execute the Python script to set up the data lake:
```bash
python3 nba_data_lake.py
```
- If everything runs successfully, you should see confirmation messages indicating that:
  - AWS resources were created successfully
  - Sample data was uploaded
  - The data lake setup is complete
 
## **Step 5: Verify AWS Resources**
### **Check the S3 Bucket**
1. In the AWS search bar, type **S3** and open the **S3 service**.
2. Locate the bucket named **`sports-analytics-data-lake`**.
3. Click on the bucket name and verify that it contains three objects.
4. Navigate to the `raw-data` folder and confirm the presence of **`nba_player_data.json`**.
5. Click the file name, then select **"Open"** to preview the data.

### **Query Data in Amazon Athena**
1. Open **Amazon Athena** in the AWS console.
2. Run the following SQL query:
   ```sql
   SELECT FirstName, LastName, Position, Team
   FROM nba_players
   WHERE Position = 'PG';
   ```
3. Click "Run"
4. Scroll down to "Query Results" to verify that the output displays player data.

## **Step 6: What We Learned**
- 🔹 Securing AWS services using IAM policies with the least privilege principle.
- 🔹 Automating AWS resource creation using Python scripts.
- 🔹 Integrating external APIs into cloud-based workflows.
  
## **Step 7: Future Enhancements**
- 🚀 Automate Deployment with AWS CloudFormation or Terraform to provision resources easily
- 🚀 Implement Role-Based Access Control (RBAC) with AWS IAM to restrict access to resources
- 🚀 Secure API Keys & Credentials using AWS Secrets Manager instead of storing them in .env
- 🚀 Integrate Machine Learning Models using AWS SageMaker to predict NBA player performance.
