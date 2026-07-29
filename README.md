# Job Portal Management System

jobs = [
    {"id": 1, "title": "Software Developer", "company": "Tech Solutions", "location": "Hyderabad", "salary": "₹6 LPA"},
    {"id": 2, "title": "Data Analyst", "company": "Data Corp", "location": "Bangalore", "salary": "₹5 LPA"},
    {"id": 3, "title": "Graphic Designer", "company": "Creative Studio", "location": "Chennai", "salary": "₹4 LPA"},
    {"id": 4, "title": "Accountant", "company": "Finance Hub", "location": "Mumbai", "salary": "₹4.5 LPA"},
    {"id": 5, "title": "Python Developer", "company": "Code World", "location": "Pune", "salary": "₹7 LPA"}
]

applications = []

while True:
    print("\n========== JOB PORTAL ==========")
    print("1. View Available Jobs")
    print("2. Search Job")
    print("3. Apply for a Job")
    print("4. View My Applications")
    print("5. Exit")

    choice = input("Enter your choice: ")

    if choice == "1":
        print("\nAvailable Jobs")
        print("-" * 75)
        print("ID\tJob Title\t\tCompany\t\tLocation\tSalary")
        print("-" * 75)
        for job in jobs:
            print(f"{job['id']}\t{job['title']}\t{job['company']}\t{job['location']}\t{job['salary']}")

    elif choice == "2":
        keyword = input("Enter job title to search: ").lower()
        found = False
        for job in jobs:
            if keyword in job["title"].lower():
                print("\nJob Found")
                print(f"ID: {job['id']}")
                print(f"Title: {job['title']}")
                print(f"Company: {job['company']}")
                print(f"Location: {job['location']}")
                print(f"Salary: {job['salary']}")
                found = True
        if not found:
            print("No matching job found.")

    elif choice == "3":
        job_id = int(input("Enter Job ID: "))

        selected = None
        for job in jobs:
            if job["id"] == job_id:
                selected = job
                break

        if selected:
            name = input("Enter Name: ")
            age = input("Enter Age: ")
            qualification = input("Enter Qualification: ")
            email = input("Enter Email: ")
            phone = input("Enter Phone Number: ")

            applications.append({
                "name": name,
                "age": age,
                "qualification": qualification,
                "email": email,
                "phone": phone,
                "job": selected["title"],
                "company": selected["company"]
            })

            print("\nApplication Submitted Successfully!")
        else:
            print("Invalid Job ID.")

    elif choice == "4":
        if len(applications) == 0:
            print("No applications submitted.")
        else:
            print("\nMy Applications")
            print("-" * 60)
            for app in applications:
                print(f"Name          : {app['name']}")
                print(f"Age           : {app['age']}")
                print(f"Qualification : {app['qualification']}")
                print(f"Applied Job   : {app['job']}")
                print(f"Company       : {app['company']}")
                print(f"Email         : {app['email']}")
                print(f"Phone         : {app['phone']}")
                print("-" * 60)

    elif choice == "5":
        print("Thank you for using Job Portal!")
        break

    else:
        print("Invalid Choice! Please try again.")
