# Google Cloud Load Balancing: Global High Availability for KidFlix Application


## Implementation of Cloud Load Balancing between Regions in the US and Europe for global high availability and intelligent traffic distribution based on user Proximity and location.

<p align="center">
<img src="https://i.imgur.com/I6xIo7N.png" height="80%" width="80%" alt="Pic"/>
<br />
<br />

## Project Overview:

In this hands-on project, Kidflix an application similar to Netflix but tailored specifically for children will be deployed across multiple global regions using Google Cloud's infrastructure. The goal is to design and implement a cloud load balancing solution that provides high availability and intelligent traffic distribution based on user proximity. This will ensure that users across the United States and Europe experience low latency and reliable service regardless of their location.

The Kidflix application is hosted in two main regions: Finland (for European users) and the United States (for American users). The solution uses Google Cloud's Cloud Run for a fully managed, serverless platform, allowing Kidflix to scale automatically without managing the underlying infrastructure. The project includes configuring a global load balancer that will route user requests to the nearest server, ensuring optimal performance.

The intelligent load balancer checks each user's location and routes their request to the closest region—users in Europe are routed to the Finland-based servers, while users in the US are routed to the US-based servers. This design improves latency for users on both continents and provides resilience; if one region becomes unavailable, traffic will be rerouted to the available region, maintaining service continuity.

## Tools and Technologies

- **Google Cloud Run**: For running the Kidflix application in a serverless environment, allowing for automatic scaling and management.
- **Google Cloud Load Balancing**: To distribute traffic between the US and European regions based on user location, ensuring low latency and high availability.
- **Google Cloud IAM**: For access and security management across regions.
- **Google Cloud Monitoring**: To track the application's health, latency, and uptime across the different regions.
- **Google Cloud Logging**: For logging requests and tracking performance to help identify and troubleshoot issues.
- **Google Cloud DNS**: For domain name management, directing users to the correct regional load balancer endpoints.

## Project Solution

The solution involves deploying KidsFlix instances in two geographically separated regions, namely Finland (Europe) and the USA. By leveraging Google Cloud Load Balancing, the system intelligently directs user traffic based on proximity and location, providing low-latency access to the application. In case of regional failures or spikes in demand, the load balancer ensures seamless redirection to the available region, guaranteeing uninterrupted service for users.

1. **Set Up Cloud Run in Each Region**: The Kidflix application was deployed in the US and Finland regions on Google Cloud Run. This approach allowed Kidflix to leverage Google's serverless capabilities, providing scalability without manual intervention.
2. **Configure Cloud IAM for Secure Access**: Permissions were set up to ensure only authorized users and services could access the application resources in each region.
3. **Regional Instance Monitoring**: Google Cloud Monitoring was enabled for each regional instance to track application health and ensure that both deployments remained accessible and performant.

## Step by Step Instructions 

### Steps for Google Cloud Setup:

#### Google Cloud Account:
- If you don't have a Google Cloud account, sign up for one at [Google Cloud Platform](https://cloud.google.com/).

#### Google Cloud Console:
- Access the Google Cloud Console (https://console.cloud.google.com/).

#### Create a New Project:
- Create a new Google Cloud Project through the Cloud Console.

### Part 1: Application Deployment and Configuration

#### Enable Cloud Run API
- Before starting the deployment process, ensure that the Cloud Run API is enabled. Navigate to the API & Services Dashboard in the Google Cloud Console, search for "Cloud Run API," and enable it if not already enabled.

<p align="center">
<img src="https://i.imgur.com/gkJcH1z.png" height="80%" width="80%" alt="Pic"/>
<br />
<br />

#### Downloading Application Files:
- In the Cloud Shell, execute the following commands to download and unzip the application files for Finland and the USA:

<p align="center">
<img src="https://i.imgur.com/1QGarmc.png" height="80%" width="80%" alt="Pic"/>
<br />
<br />

<p align="center">
<img src="https://i.imgur.com/9XBTJl4.png" height="80%" width="80%" alt="Pic"/>
<br />
<br />

<p align="center">
<img src="https://i.imgur.com/dFLwupH.png" height="80%" width="80%" alt="Pic"/>
<br />
<br />

<p align="center">
<img src="https://i.imgur.com/BUD4WUv.png" height="80%" width="80%" alt="Pic"/>
<br />
<br />

#### Application Deployment Kid Flix: Finland
- Navigate to the Finland application folder and build the container image using Cloud Build. Deploy the application on Cloud Run in the Europe-North1 region.

##### Step 1) Accessing the folder of the Finland application files

<p align="center">
<img src="https://i.imgur.com/X9vOSDG.png" height="80%" width="80%" alt="Pic"/>
<br />
<br />

##### Step 2) Running the Cloud Build in the container image

<p align="center">
<img src="https://i.imgur.com/dCbLDRz.png" height="80%" width="80%" alt="Pic"/>
<br />
<br />

##### Step 3) Deploying the application using the Cloud Run.
- Press Enter to confirm the default application name: appkidsflixfinland
- Select the region, europe-north1, typing the number: 13
- Allow unauthenticated requests by typing: y

<p align="center">
<img src="https://i.imgur.com/c74uQoD.png" height="80%" width="80%" alt="Pic"/>
<br />
<br />

<p align="center">
<img src="https://i.imgur.com/bxSLhcb.png" height="80%" width="80%" alt="Pic"/>
<br />
<br />

#### Verify Deployments
Access the URLs provided for the Finland and USA applications to verify that they are up and running successfully. The URLs will display the Kids Flix application, and the flags in the footer will indicate the region (Finland or USA).

<p align="center">
<img src="https://i.imgur.com/BpLvMoS.png" height="80%" width="80%" alt="Pic"/>
<br />
<br />

<p align="center">
<img src="https://i.imgur.com/kShJu47.png" height="80%" width="80%" alt="Pic"/>
<br />
<br />

<p align="center">
<img src="https://i.imgur.com/2wtRJZt.jpeg" height="80%" width="80%" alt="Pic"/>
<br />
<br />

<p align="center">
<img src="https://i.imgur.com/BcSgVuV.png" height="80%" width="80%" alt="Pic"/>
<br />
<br />

<p align="center">
<img src="https://i.imgur.com/kinwwM4.png" height="80%" width="80%" alt="Pic"/>
<br />
<br />

#### Application Deployment KidFlix: USA
- Navigate to the USA application folder and build the container image using Cloud Build. Deploy the application on Cloud Run in the US-Central1 region.

##### Step 1) Accessing the folder of the USA application files

<p align="center">
<img src="https://i.imgur.com/xiyvymt.png" height="80%" width="80%" alt="Pic"/>
<br />
<br />

##### Step 2) Running the Cloud Build in the container image

<p align="center">
<img src="https://i.imgur.com/9BvZeOg.png" height="80%" width="80%" alt="Pic"/>
<br />
<br />

##### Step 3) Deploying the application using the Cloud Run.
- Press Enter to confirm the default application name: appkidsflixusa
- Select the region, us-central1, typing the number: 32
- Allow unauthenticated requests by typing: y

<p align="center">
<img src="https://i.imgur.com/Nj3Cnzq.png" height="80%" width="80%" alt="Pic"/>
<br />
<br />

<p align="center">
<img src="https://i.imgur.com/vP8FepH.png" height="80%" width="80%" alt="Pic"/>
<br />
<br />

#### Verify Deployments
Access the URLs provided for the Finland and USA applications to verify that they are up and running successfully. The URLs will display the Kids Flix application, and the flags in the footer will indicate the region (Finland or USA).

<p align="center">
<img src="https://i.imgur.com/T9z6KoO.png" height="80%" width="80%" alt="Pic"/>
<br />
<br />

<p align="center">
<img src="https://i.imgur.com/d9UQ43M.png" height="80%" width="80%" alt="Pic"/>
<br />
<br />

<p align="center">
<img src="https://i.imgur.com/ae6boUC.png" height="80%" width="80%" alt="Pic"/>
<br />
<br />

<p align="center">
<img src="https://i.imgur.com/x9W7v93.png" height="80%" width="80%" alt="Pic"/>
<br />
<br />

<p align="center">
<img src="https://i.imgur.com/M0lJsWr.png" height="80%" width="80%" alt="Pic"/>
<br />
<br />

### Part 2: Configuring the Global Load Balancer for Intelligent Traffic Distribution

The next step involved setting up a global load balancer to route users based on their geographic location. This load balancer was configured to automatically direct user requests to the nearest server, either in the US or Finland, ensuring minimal latency and an optimal experience.

1. **Set Up Google Cloud Load Balancer**: A global load balancer was configured to route user requests intelligently based on user proximity.
2. **Traffic Routing Rules Based on Location**: The load balancer was configured to check each user's location upon receiving a request. Users from Europe were routed to the Finland-based instance, while users from the US were directed to the US-based instance.
3. **Failover Mechanism**: The load balancer was designed with failover rules, allowing traffic to be rerouted to the other region if one region becomes unavailable. This ensured continuous service availability even during regional disruptions.
4. **Testing and Validation**: Tests were conducted to confirm that users in different locations were routed to the correct instances and that failover routing worked as expected.

#### Deploying of the External HTTP Load Balancer

##### Step 1) Creating 2 serverless Network End Groups (NEG)

<p align="center">
<img src="https://i.imgur.com/mLjbsVL.png" height="80%" width="80%" alt="Pic"/>
<br />
<br />

<p align="center">
<img src="https://i.imgur.com/kIqv1RH.png" height="80%" width="80%" alt="Pic"/>
<br />
<br />

##### Step 2) Creating the backend service global 
- Create a global backend service that spans multiple regions.

<p align="center">
<img src="https://i.imgur.com/9LMfGSB.png" height="80%" width="80%" alt="Pic"/>
<br />
<br />

##### Step 3) Adding the serverless NEG created to the backend service global
- Add the network endpoint groups to the global backend service.
- Add Finland backend
- Add USA backend

<p align="center">
<img src="https://i.imgur.com/58ib45R.png" height="80%" width="80%" alt="Pic"/>
<br />
<br />

##### Step 4) Creating an URL map to redirect the incoming requisitions to the backend service
- Create a URL map for routing requests. This is a prerequisite for multiregional load balancing.

<p align="center">
<img src="https://i.imgur.com/yNDeZBQ.png" height="80%" width="80%" alt="Pic"/>
<br />
<br />

##### Step 5) Creating the target HTTP(S) proxy to redirect the requisitions to the URL map

<p align="center">
<img src="https://i.imgur.com/d05Lw1q.png" height="80%" width="80%" alt="Pic"/>
<br />
<br />

##### Step 6) Reserving an IP address to the External HTTP Load Balancer

<p align="center">
<img src="https://i.imgur.com/SAO3JIB.png" height="80%" width="80%" alt="Pic"/>
<br />
<br />

##### Step 7) Check Reserved IP
- Check the reserved IP address that was created for the load balancer.

<p align="center">
<img src="https://i.imgur.com/4fFSvhr.png" height="80%" width="80%" alt="Pic"/>
<br />
<br />

##### Step 8) Create Global Forwarding Rule
- Create a global forwarding rule to direct incoming requests to the target HTTPS proxy (Frontend).

<p align="center">
<img src="https://i.imgur.com/0lNDDuM.png" height="80%" width="80%" alt="Pic"/>
<br />
<br />

##### Step 9) Verification
- After executing the commands, wait for a few minutes until the load balancer is fully provisioned. Access the provided IP address in a browser to ensure successful access. The load balancer should route requests based on geographical proximity.

<p align="center">
<img src="https://i.imgur.com/wcoZ72T.png" height="80%" width="80%" alt="Pic"/>
<br />
<br />

<p align="center">
<img src="https://i.imgur.com/xlpOC0b.png" height="80%" width="80%" alt="Pic"/>
<br />
<br />

<p align="center">
<img src="https://i.imgur.com/2cGkSEk.png" height="80%" width="80%" alt="Pic"/>
<br />
<br />

#### Testing from Different Regions
- To test the load balancing based on geographical location, use a VPN to simulate connections from different regions. 
- Verify that, based on the VPN location, the load balancer redirects to the corresponding region (Finland or USA).

<p align="center">
<img src="https://i.imgur.com/sBSUHne.png" height="80%" width="80%" alt="Pic"/>
<br />
<br />

<p align="center">
<img src="https://i.imgur.com/0BDuD9B.png" height="80%" width="80%" alt="Pic"/>
<br />
<br />

<p align="center">
<img src="https://i.imgur.com/euKnzK8.png" height="80%" width="80%" alt="Pic"/>
<br />
<br />

## Project Conclusion

The Kidflix project successfully demonstrated how to build a global, resilient, and scalable application using Google Cloud services. By deploying across multiple regions and implementing a global load balancer, Kidflix achieved high availability, optimized performance, and robust failover capabilities. The serverless nature of Cloud Run reduced operational overhead, allowing the application to scale effortlessly with demand.

### Challenges Encountered
- **Latency Optimization for Traffic Routing**: Fine-tuning the load balancer settings to ensure optimal latency for users required testing and adjustments.
- **Configuration of Failover Mechanisms**: Setting up failover to ensure seamless user experience in case of regional outages posed some challenges, as the balance between failover speed and reliability needed to be achieved.

### Lessons Learned
- **Proximity-Based Load Balancing**: Proximity-based traffic routing was effective in improving user experience, highlighting the benefits of strategically placing resources close to end-users.
- **Importance of Regional Redundancy**: Distributing resources across regions proved essential for high availability and resilience.
- **Effective Use of Serverless Services**: Google Cloud Run's serverless features significantly reduced deployment complexity and operational overhead.

### Future Improvements
- **Enhanced Monitoring and Logging**: Implementing more granular monitoring and logging could improve insights into user behavior and latency issues.
- **Expansion to Additional Regions**: To further improve latency, adding more regional deployments could provide even faster response times for users in other continents.
- **Advanced Failover Configurations**: Additional failover configurations, such as weighted load balancing, could provide more precise control over traffic distribution, especially during peak times or partial outages.
