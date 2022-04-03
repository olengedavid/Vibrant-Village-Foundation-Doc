# VIBRANT VILLAGE FOUNDATION

> Vibrant village Foundation is an organization based in Portland, Oregon and USA, it provide grunds for  community based projects that aims to elevate familie's living standards by improving food security, family health, financial wellbeing and education.


![screenshot](vvfhome.png)



In kenya, Vibrant Village Foundation works with a community based in Western who are majorly farmers. Farming being one of the economic activities in the area, the organization invested in empowering farmers through quality seeds, fartelizers and farm tools. To manage all these resources, there was a need to centralize control and monitor the progress of these products, leading to development of Vibrant Village Foundation Portal.

### Built With

- Major languages: Elixir
- Frameworks: Phoenix, PhoenixLiveView, MaterializeCss
- Technologies used: web technologies(HTML, CSS and JS)

### Live Demo

[Live Demo Link](working-of-the-system.gif) #screen recording of how the app works


# Getting Started

To get a local copy up and running follow these simple example steps.

### Prerequisites

- Elixir 1.12.1
- Erlang/OTP 24
- nodejs > 12 LTS
- PostgreSQL 12.7 
- Hex, Elixir's package manager


### Install
- Clone the project using `git clone url`
- For elixir and phoenix development environment use [the phoenix installation guide](https://hexdocs.pm/phoenix/installation.html#content) to ensure everything is setup as expected.

### Setup
 - **Start Server**

To run your phoenix server:

* Run `mix deps.get` to fetch and install dependecies.
* Run seeds, create and migrate your database with `mix ecto.setup`
* Install Node.js dependecies with `npm install` inside the `assests` directory.
* Start all your application endpoints with `mix phx.server`

Now visit `http://localhost:4000/farming` from your browser to visit the login page.

Use these credentials to login:
* Email: `admin@gmail.com`
* Password: `admin`

# Usage
## FAEMER REGISTRATION

Farmer can be registered through the following channels:
  1. Kobo.
  2. SMS.
  3. USSD.
  4. Web.

**1. SMS**

The farmer is asked a series of questions that they need to answer. All these data is temporarily stored in database table which is then transfered to the main farmers table upon completion.

**Technical steps**

| Step | Description|
| -----| -----------|
|1     |Welcome farmer and ask  for the farmer national id|
|2     |Ask for the names|
|3     |The year of birth|
|4     |Their phone number|
|



A farmer who initiates registration process is automatically at `step0` of registration. When they resume the process, question for `step1` will be asked. This means that the questions we ask the farmer is always  a step a head of the step we have in the database.

**2. KOBO**

[KoBoToolbox](https://support.kobotoolbox.org/new_form.html) is a free and open source software that is used for field data collection. The field officers use the kobo forms to collect farmer data which are later transmitted to Vibrant repo via a webhook.

The data can be collected while the devices are offline and be transmitted once the device get connected to the internet.

**koBo farmer registration form format**
- farmer name as it appearson the id card.
- farmer year of birth.
- national id.
- farmer's nearest school.
- phone number.
- sublocation.
- please take gps of home if possible .
- farmer gender.
- deviceId.
- group leader Id.
- nok name.
- nok id.
- nok gender.
- realationship 
- nok year of birth.


The form ensure data integrity rules are adhered to which reduces errors leading to better quality data.

**3. WEB**

Registered farmers can be divided into stations based on locality and groupes according to  shared interest. A farmer's next of kin details are also captured to determine inheritance rights if a person dies. Farmers index page can display all farmers on variation of options, such as : qualified, non-qualified, sales group, groupless and registered farmers.

This page shows the details required to register a farmer.


![Farmer Registration](vvfFarmer_reg.png)

## STATION REGISTRATION

Stations are formed from farmers living within demacated geograohical area, headed by a particular farmer. The page below shows the details needed to register a station.

![Station registration](vvf_station-_reg.png)

## NEXT OF KIN REGISTRATION

In Kenya next of kin is a person's closest living relative who can be contacted incase of any enventuality. This person can be registered during farmer registration on the `farmer registration` form, or added to an existing farmer on the `farmer edit` form. Different types of relationship that exist between a farmer and NOK are captured on a `Nok Relationships` form and populated during farmer registration. Once registered all NOks can be viewed on the Nok of kins tab.

![NOK registration](NOK.png)

# SYSTEM USERS

These are people with their own user name and password granted access to perform an organization tasks within a system. Vibrant have five levels of users, super admin, admin, field officer and intern, with super admin having the highest preveleges. Below is the form used to create users.

![User registration](user.png)

Role management or user access control is implemented in two ways: Through plugs and pipelines and data base role designation.  All users page contain options to edit details, activate/deactive, show user actions and submitted payments for field officers. Show user actions button display a  modal indicating actions for a particular resource(e.g farmer, order).


![User role checkbox](user_roles.png)

## ORDERS
These are the individual farm commodities that a registered farmer can order and pay back the due amount within a stepulated time. The available order types include:
- Package.
- Individual Items.
- Top up.
- Short rain.

Order creation process through the web i.e vibrant application inolves a serries of steps.

|step|Description|
|----|-----------|
|1   |Choose a registered active farmer|
|2   |Select the type of order|
|3   |Add discount(optional)  |
|4   |Click creat order|

The different type of orders have different ways of creating them.
**Package type**

|step| Description|
|----|------------|
|1   |Select type of order(package)|
|2   |Select a package(seed and other packages)|
|3   |Seed packages(1 seed, 2 seed e.t.c)|
|4   |Select main seed|
|5   |Select extra seed|
|6   |back to step three of order creation|

For the remaining order types you are presented with a search bar that populates all the available order types and option to specify the number of bags needed. The search is matched according to the names.

**Package Type and Products**


Products are individual items which can be ordered. They are specified into different categories: maize seed, other fertilizer, other items, planting fertilizer, and top dressing fertilizer. On the other hand packages are bundles of these indidivual products.e.g one seed package contains: 1 seed, 1 Dap(10)kg, 2 Can(10)kg, Benevolent Fund, Sukuma(10)g.   

## PAYMENTS

Farmers make payments through mpesa in a given account number. The mpesa details are extracted into a csv format and feed into the system to be processed and pay for the farmer order, in accordance to the business logic. The payments can be in different status: success, flagged, failed, new and in progress. Once the payment has paid for the intended order, a message is sent back to the farmer, describing what he/she has paid for, amount, the due balance and the percentage paid.

When payment gets into the system it is referred as incoming payment and stored into incoming payment table before it is processed. If the farmer had an open order which  isn't fully paid, the incoming payment will be processed to pay for the order, at this point it is called repayment.

However if the farmer had no open order, the incoming payment will be stored in excess payment table, from which it can be refunded to the farmer or pays for the farmer order in future.

If the farmer pay until it exceeds the order amount, that payment is labelled as excess. It is kept within the system unless the farmer request for a refund. The refund is recorded and approved after which it is manually sent back to the farmer.

The dashboard offers good options to view all, order, failed, excess and  refunded payments. Additionaly loan repayment report for a specific station can be listed.

**RECORD REFUND**

A farmer may have excess amount in the system based on the two conditions described above, after which the farmer might like to request for a refund. This process is done is the following three stages:

  1. Request refund: A request is made to refund a farmer a certain amount, this is also the point the money from excess is deducted in the database.
  2. Approve refund: The authorized user cross-check the records displayed and confirms that these are the exact details of the farmer and the phone number the refunded amount should be sent to.
  3. Mark as paid: After the specified amount is sent to the farmer, the receipt and date the money was sent to the farmer are captured to mark the end of the process.

- [Record refund process](record_refund.gif) #live demo of how the refund process is done
## DEADLINES

For computerized systems these are points in time, by which an objective must be accomplished, after which the functionality to perform that task is disabled. As of this time, vibrant has three different deadlines that can be set, namely seed verification, credit qualification and individual order.

## DEVICES

These are electronic gadgets in the form of mobile phones or tablets assigned to vibrant users. Due to the dispersed and dynamic nature of customers and work, their was a need to localize services such as farmer registration to the actual location of the farmer, where surveys and geolaction of the farm can be done. Most of these actions are performed by field officers who get assigned these devices. TO register or acquire a device, the device ID and user must be provided, it must also be indicated if the device is being used or not.

## REPORTS

These are statitistical summary on specific business parameters that can provide important details to help design future forcasts, marketing plans, guide budgeting plans and improve decision making. Vibrant has quartely reports which comprise of sales and credit reports,top up summary entails reports for different order items based on active, inactive and delivered status.

## SEASONS
Vibrant organization operate on a time interval of seasons when it comes to providing orders to farmers. Farmers have to request for orders before the start of the season, after which they are given at the onset of the season. Payment of these orders is expected to be completed before the end of the season, otherwise the farmer is labelled as a defaulter. 


* Super admin
    - 
* Admin
    - 
* Field Officer
    -
* Intern
    -

### Run tests

### Deployment



## Authors



👤 ****

## 🤝 Contributing

We use [semantic version](https://semver.org/)to keep track of the application builds.

👤 **FRANK MIDIGO**

- Github: [@githubhandle](https://github.com/MidigoF)
- Twitter: [@twitterhandle](https://twitter.com/midigo_frank)
- Linkedin: [linkedin](https://www.linkedin.com/in/midigo-f-023450123/)
## Issue tracking
We create user stories in Jira and link them up on Trello. Check vibrant [Trello board](https://trello.com/b/8dQkIYUt/vibrant-tasks) indicating how we track issues from `To Do` to `staging`. 




Contributions, issues and feature requests are welcome!

Feel free to check the [issues page](issues/).

## Show your support

Give a ⭐️ if you like this project!

## Acknowledgments

- Hat tip to anyone whose code was used
- Inspiration
- etc

## 📝 License

This project is [MIT](lic.url) licensed.
