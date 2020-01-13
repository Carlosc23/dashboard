# dashboard

This project is as simple dashboard to retrieve dummy data for clients who spent money in bank. Initial work was with a demo of ZingChart.

### Installing

To use this project, first you need to install [Node](https://nodejs.org/es/).

Then, clone this repository.

    $ git clone https://github.com/Carlosc23/dashboard/
    $ cd <dir where you have dowloaded the project>/dashboard

After being located in the project in cmd, run:

```
npm i
```
This command will install all the necessary packages to use and run the project.
Then, run the application:

	$ npm run serve

To see your application, access this url in your browser: 

	http://localhost:8080
## Built With

* [Vue](https://vuejs.org/).- The javascript library used.
* [ZingChart](https://www.zingchart.com/)- Framework for charts.
* [Axios](https://github.com/axios/axios)- Module to consumo API.

## Project structure
After you clone, install packages and run it. You may want to know the structure of the project. Basically, the structure is this:
```
  ├── react-boilerplate
    │   ├── dist
    │   ├── src
    	 │   ├── components
         │   ├── theme
	 │   ├── App.vue
	 │   ├── main.js
    │	├── .babelrc
    │	├── .eslintrc
    │	├── .gitignore
    │	├── package.json
    │	├── README.md
```
`dist` refer to the folder where webpage in production will be stored.

`src` is the folder where the code and files of js,vue will be stored.

`components` is the folder where the components of the dashboard are stored.

`App.vue` Principal module who use the components, and make axios call to api

`main.js` Module where main libraries are called

`.babelrc`    Tanspiler

`gitignore`   File to ignore all heavy or unnecessry packages.

`package.json` File where are listed all the necessary packages that need the project to run.

`README.md`   Instructions and description of the project.


## Authors

* **Carlos Calderon** - *Initial work*

## License

This project is licensed under the MIT License - see the [LICENSE.md](LICENSE.md) file for details

### Customize configuration
See [Configuration Reference](https://cli.vuejs.org/config/).

