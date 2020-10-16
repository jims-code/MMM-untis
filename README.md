
# MMM-untis
This an extension for the [MagicMirror](https://github.com/MichMich/MagicMirror). It allows to display your kids' lessons for schools using [Untis](https://www.untis.at) software to organize school's timetables. You are able to configure acccess for each of your kids.

# Origin
This module ist work-in-progress. It is baesd on MMM-Webuntis from thyed (https://github.com/thyed/MMM-Webuntis). THANK YOU SO MUCH FOR YOUR WORK - I AM SO HAPPY THAT I CAN START DEVELOPING ON THIS BASE!

# ....The following documentation needs to be rewritten...

## Installation
1. Navigate into your MagicMirror's `modules` folder and execute `git clone https://github.com/jims-code/MMM-untis.git`.
2. Navigate into the new folder `MMM-Webuntis` and execute `npm install` to generate the node dependencies.

## Using the module

To use this module, add it to the modules array in the `config/config.js` file:
```javascript
modules: [
	{
		module: "MMM-Webuntis",
		position: "top_right",
		header: "Untis",
		config: { // see 'Configuration options' for more information
			students: [
				{
					title: "1st child's name",
					school: "your school",
					username: "your untis username",
					password: "your untis password",
					server: "untis server"
				},
				{
					title: "2nd child's name",
					school: "your school",
					username: "your untis username",
					password: "your untis password",
					server: "untis server"
				},
			],
			days: 1, // number of days to look ahead
			fetchInterval: 5*60*1000, // update intervall in milliseconds
			showStartTime: false // whether to show lesson number ('1.') or time ('07:40')
		}
	}
```

## Configuration options

The following properties can be configured:


<table width="100%">
	<thead>
		<tr>
			<th>Option</th>
			<th width="100%">Description</th>
		</tr>
	<thead>
		<tr>
			<td><code>students</code></td>
			<td>
				Array of untis login credentials objects</br></br>
				<b>Possible values:</b> <code>array</code> of objects with the following attributes:
				<table>
					<tr>
						<td><code>title</code></td>
						<td>Title of the entry, e.g. kid's name</td>
					</tr>
					<tr>
						<td><code>school</code></td>
						<td>School name as in the URL after having logged in at <a href="https://webuntis.com/">webuntis.com</a>. A plus sign (+) in the URL can be replaced by space.</td>
					</tr>
					<tr>
						<td><code>username</code></td>
						<td>Username used to login at Untis</td>
					</tr>
					<tr>
						<td><code>password</code></td>
						<td>Password used to login at Untis</td>
					</tr>
					<tr>
						<td><code>server</code></td>
						<td>Server as shown in the URL after having loged in at <a href="https://webuntis.com/">webuntis.com</a>, e.g. <code>kephiso.webuntis.com</code>
				</table>
			</td>
		</tr>
		<tr>
			<td><code>days</code></td>
			<td>
				Number of days to look ahead</br></br>
				<b>Possible values:</b> <code>int</code> from <code>1</code> to <code>10</code></br>
				<b>Default value:</b> <code>7</code>
			</td>
		</tr>
		<tr>
			<td><code>fetchInterval</code></td>
			<td>Defines how often the module shall retrieve data from Untis<br>
				<br><b>Possible values:</b> <code>int</code> in milliseconds
				<br><b>Default value:</b> <code>5*60*1000</code>
			</td>
		</tr>
		<tr>
			<td><code>showStartTime</code></td>
			<td>Whether time or lesson order number shall be shown<br>
				<br><b>Possible values:</b> <code>true</code> or <code>false</code>
				<br><b>Default value:</b> <code>false</code></br></br>
				The module tries to achieve the timetable of the school and currently assumes that Monday's lesson times are valid for the whole week. When set to <code>false</code> the module matches a start time like "07:40" to "1." for example.
			</td>
		</tr>
</table>

## How it works
This module may be useful for students at schools using Untis for the organization of time tables. It uses the node.js wrapper of the WebUnits API by TheNoim and retrieves all lessons in a specified number of days time period. It displays cancelled or irregular subjects so that kids are able to prepare for the next day without pulling the information from the Untis app. The module can be configured for several students.

## Dependencies
- [node.js Wrapper for WebUntis API](https://github.com/TheNoim/WebUntis) (installed via `npm install`)


## Screenshots
![Screenshot](screenshot.png "Screenshot")

## Attribution

This project is based on work done by Paul-Vincent Roll in the MMM-Wunderlist module. (https://github.com/paviro/MMM-Wunderlist)
