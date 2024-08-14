## Background
SAP Equipment and Characteristics Sharepoint List is used as a repository where users can upload equipment changes (new installation, old euquipment removal, parameter update). Flat files are generated using the data from this Sharepoint list upon request and they will be sent along a SAP Master Data notification in SAP to update SAP Master Data. </br>

This repository is becoming increasing large and causes the performance of its related services to degrade. As list items that have flat files already generated will no longer be used in the list, this archive flow is created to delete the list items and store them in the archive folder.

## Flow Diagram
![image](https://github.com/user-attachments/assets/5db64607-f937-490d-9aa5-829d89358513)

![2](https://github.com/user-attachments/assets/6236965b-e4ae-43a8-ad27-f6130d738199)
