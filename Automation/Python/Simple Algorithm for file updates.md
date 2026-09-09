Project description
This script updates an IP allow list during firewall migration. It reads your allow list file, removes any IPs you specify, and saves the updated list back. It's straightforward, easy to follow, and perfect for learning.


Create a file named allow_list.txt in the same folder as your Python script, and paste this content:

#Allowed IP Address List - Firewall Migration
#Format: One IP or CIDR range per line

10.0.0.0/8
172.16.0.0/12
192.168.0.0/16
192.168.1.0/24
192.168.2.0/24
10.0.0.5
10.0.0.12
172.31.0.10
203.0.113.5
203.0.113.10

#End of list

## Open the file that contains the allow list
    # Open the allow list file
    with open("allow_list.txt", "r") as file:
## Read the file contents
    # Read all content from the file
    content = file.read()
## Convert the string into a list
    # Split content line-by-line and clean up extra spaces
    allow_list = [line.strip() for line in content.splitlines() if line.strip()]
## Iterate through the remove list
    # List of IP addresses you want to remove
    remove_list = [
        "192.168.1.0/24",
        "10.0.0.5"
    ]

    # Prepare a new empty list
    updated_list = []

    # Check each IP in the allow list
    for ip in allow_list:
## Remove IP addresses that are on the remove list
    # Keep IPs that are NOT in the remove list
    if ip not in remove_list:
        updated_list.append(ip)
## Update the file with the revised list of IP addresses 
    # Write the cleaned list back to the file
    with open("allow_list.txt", "w") as file:
        file.write("\n".join(updated_list) + "\n")

    print("Allow list updated successfully!")

 
## Summary
This simple script opens and reads your allow list file, then turns the text content into a list of IP addresses. It goes through each address one by one and removes the ones you have listed for removal. Finally, it saves the updated list of IP addresses back to your file.

#H ow to Practice
1.	Save the sample content above into allow_list.txt
2.	Copy the Python code into a file like update_allowlist.py
3.	Run it: python update_allowlist.py
4.	Open allow_list.txt — you'll see those two IPs are gone!
5.	Try adding more IPs to remove_list and run it again
