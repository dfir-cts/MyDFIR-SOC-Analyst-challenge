# Day 1 : Creating a Logical Network Diagram using Draw.io

Draw.io is a free, open-source diagramming tool that allows users to create a wide variety of diagrams, flowcharts, and visual representations. It's a web-based application, which means it can be accessed directly through a web browser without the need for installation. However, it also offers desktop versions for those who prefer offline use. 
Key features include:
1.	Web-based and desktop applications
2.	Extensive library of shapes and icons
3.	Collaboration tools for team projects
4.	Export options in multiple formats (PNG, SVG, PDF, etc.)
5.	Integration with cloud storage services
6.	Version control and revision history

Step-by-step guide to creating the diagram:
## 1: Set up the draw.io canvas
1.	Go to draw.io (https://app.diagrams.net/), you must log in first
2.	Click on "Create New Diagram"
3.	Choose "Blank Diagram", 
4.	Rename diagram name to "30-day MyDFIR Diagram" and click "Create"
![image](https://github.com/user-attachments/assets/fe40aeed-365f-49ff-9c6b-ecf257c71b2a)

## 2: Add the server
1.	From the left sidebar, search for "server" in the shape library
2.	Drag and drop a server icon onto the canvas.
3.	Duplicate the server icon to create 6 servers in total.
4.	Label the servers as follows:
•	Elastic and Kibana
•	Windows Server RDP enabled
•	Ubuntu Server SSH enabled
•	Fleet Server
•	OS Ticket Server
5.	add C2 server and color the C2 server in red to highlight potential threats.
![image](https://github.com/user-attachments/assets/87b7e8cf-d72a-41ac-8e42-f86793b8a089)

## 3: Creating the Cloud Environment 
1.	Add a rounded rectangle to represent Vultr cloud provider.
2.	Label it "Vultr" and position it behind the servers.
3.	Add a VPC shape to encompass the servers.
![image](https://github.com/user-attachments/assets/9b78a91c-73ea-493a-b3fd-e187bbb006e3)

## 4.	Connecting Components
1.	Use arrows to connect the Windows and Ubuntu servers to the Fleet Server.
2.	Connect the Fleet Server to Elastic and Kibana.
3.	Link OS Ticket to Elastic and Kibana.
4.	Connect Windows and Ubuntu servers directly to Elastic and Kibana for log forwarding.
5.	Adjust arrow styles for clarity
6.	Label connections ("managed," "forward logs via agent").
![image](https://github.com/user-attachments/assets/62c4ce90-96c8-464d-af9a-55b01789e5a4)
 
## 5. Adding Internet Connectivity
1.	Add an Internet Gateway shape.
2.	Include a cloud shape to represent the internet.
3.	Connect the Internet Gateway to both the VPC and the internet cloud.
4.	Label the VPC with the private network range: "172.31.0.0/24"
![image](https://github.com/user-attachments/assets/1dfc142d-256e-4864-a14c-494768917c0a)

## 6. Including User Devices
1.	Add a laptop icon for the SOC Analyst.
2.	Add another laptop icon for the Attacker.
3.	Connect both laptops to the internet cloud.
4.	Add a description for the SOC Analyst connection: "Connect to Elastic & Kibana via web GU
![image](https://github.com/user-attachments/assets/c479f19c-14e5-4091-9c2f-b5275a848b97)

## 7 Saving and Exporting
1.	Click on "File" in the top left corner.
2.	Select "Save" to store your diagram.
3.	Optionally, export the diagram in your preferred format (PNG, PDF,JPEG etc.) for sharing.
![image](https://github.com/user-attachments/assets/0c949dd9-ec6a-4826-8239-f5836db1c90b)

![image](https://github.com/user-attachments/assets/fb9f63f7-1d8e-45bd-b046-9fe1632135dd)
 
By following these steps, aspiring SOC analysts can create a comprehensive logical diagram that serves as a valuable reference throughout their learning journey and future career in cybersecurity.


