# VIBRANT VILLAGE FOUNDATION

> Vibrant village Foundation is an organization based in Portland, Oregon and USA, it provide grunds for  community based projects that aims to elevate familie's living standards by improving food security, family health, financial wellbeing and education.


![screenshot](vvfhome.png)



In kenya, Vibrant Village Foundation works with a community based in Western who are majorly farmers. Farming being one of the economic activities in the area, the organization invested in empowering farmers through quality seeds, fartelizers and farm tools. To manage all these resources, there was a need to centralize control and monitor the progress of these products, leading to development of Vibrant Village Foundation Portal.

## Built With

- Major languages: Elixir
- Frameworks: Phoenix, PhoenixLiveView, MaterializeCss
- Technologies used: web technologies(HTML, CSS and JS)

## Live Demo

[Live Demo Link](working-of-the-system.gif) #screen recording of how the app works


## Getting Started

**This is an example of how you may give instructions on setting up your project locally.**
**Modify this file to match your project, remove sections that don't apply. For example: delete the testing section if the currect project doesn't require testing.**


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
**Start Server**

To run your phoenix server:

* Run `mix deps.get` to fetch and install dependecies.
* Run seeds, create and migrate your database with `mix ecto.setup`
* Install Node.js dependecies with `npm install` inside the `assests` directory.
* Start all your application endpoints with `mix phx.server`

Now visit `http://localhost:4000/farming` from your browser to visit the login page.

Use these credentials to login:
* Email: `admin@gmail.com`
* Password: `admin`

### Usage
**Farmer registration**

Registered farmers can be divided into stations based on locality and groupes according to  shared interest. A farmer's next of kin details are also captured to determine inheritance rights if a person dies. Farmers index page can display all farmers on variation of options, such as : qualified, non-qualified, sales group, groupless and registered farmers.

This page shows the details required to register a farmer.


![Farmer Registration](vvfFarmer_reg.png)

**Station Registration**

Stations are formed from farmers living within demacated geograohical area, headed by a particular farmer. The page below shows the details needed to register a station.

![Station registration](vvf_station-_reg.png)

**Next of Kin Registration**
In Kenya next of kin is a person's closest living relative who can be contacted incase of any enventuality. This person can be registered during farmer registration on the `farmer registration` form, or added to an existing farmer on the `farmer edit` form. Different types of relationship that exist between a farmer and NOK are captured on a `Nok Relationships` form and populated during farmer registration. Once registered all NOks can be viewed on the Nok of kins tab.

![NOK registration](NOK.png)

**System Users**
These are people with their own user name and password granted access to perform an organization tasks within a system. Vibrant have five levels of users, super admin, admin, field officer and intern, with super admin having the highest preveleges. Below is the from used to create users.

![User registration](user.png)

Role management or user access control is implemented in two ways: Through plugs and pipelines and data base role designation.  All users page contain options to edit details, activate/deactive, show user actions and submitted payments for field officers. Show user actions button display a  modal indicating actions for a particular resource(e.g farmer, order).


![User role checkbox](user_roles.png)


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

👤 **Author1**

- Github: [@githubhandle](https://github.com/githubhandle)
- Twitter: [@twitterhandle](https://twitter.com/twitterhandle)
- Linkedin: [linkedin](https://linkedin.com/linkedinhandle)

👤 **Author2**

- Github: [@githubhandle](https://github.com/githubhandle)
- Twitter: [@twitterhandle](https://twitter.com/twitterhandle)
- Linkedin: [linkedin](https://linkedin.com/linkedinhandle)

## 🤝 Contributing

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
