
# Auto-Scaling Web Application

Deployed a scalable web application to handle high traffic using auto-scaling and load balancing


## AWS Services
- EC2
- Auto Scaling
- Elastic Load Balancer (ELB)
- CloudWatch
## Key Achievements

- Automated EC2 scaling 
- ensured high availability with Elastic Load Balancer
- monitored performance with CloudWatch alerts.
## Image

![DR Implementation Architecture](https://i.ibb.co/L1hdGXx/1-k-Djw0r-LWPRl-Uq127-WY-h-Q.png)

## Steps

# Step1: Launch an EC2 Instance

- Go to the **EC2 Console** and click **Launch Instance**.
- Choose **Amazon Linux 2** as the operating system.
- Select **t2.micro** (free tier) as the instance type.
- Set up a **Security Group**:
    - Allow **HTTP (port 80)** for web traffic.
    - Allow **SSH (port 22)** for access.
- Click **Launch** and download the key pair for SSH access.

# Step2: Install a Web Server on EC2

- **Connect to Your Instance:** Use SSH to connect
- **Install Apache Web Server**
- **Create a Test Page:** echo "Welcome to My Scalable Web App" | sudo tee /var/www/html/index.html

# **Step3: Create a Load Balancer**

- Go to **EC2 Console > Load Balancers** > **Create Load Balancer**.
- Choose **Application Load Balancer**.
- Set up:
    - **Listener**: HTTP (port 80).
    - **Availability Zones**: Select at least 2 zones for high availability.
- Create a **Target Group** and add your EC2 instance to it.
- Complete and launch the Load Balancer.

---

# **Step4: Set Up Auto Scaling**

- Go to **EC2 Console > Auto Scaling Groups** > **Create Auto Scaling Group**.
- Use a **Launch Template**:
    - Select the AMI of your EC2 instance.
- Define Scaling Settings:
    - **Minimum Instances**: 1
    - **Desired Capacity**: 2
    - **Maximum Instances**: 5
- Attach the **Target Group** (from the Load Balancer).
- Set **Scaling Policies**:
    - Scale out when CPU usage > 70%.
    - Scale in when CPU usage < 30%.

# **Step5:  Monitor with CloudWatch**

- Go to **CloudWatch** and create alarms for CPU usage.
- Set notifications using Amazon SNS to get alerts.

# **Step6: Test the Setup**

- Copy the **Load Balancer DNS name** from the console.
- Open it in a browser to check if the test page is visible.
- Use a load testing tool to simulate high traffic and watch Auto Scaling add more instances.
