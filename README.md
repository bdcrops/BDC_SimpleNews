
# Magento 2 SimpleNews module  

**Magento 2 Module development** or **Magento 2 SimpleNews Module**  Create a full-fledged Module Step by Step. You could just follow my code to create this module from the scratch. Or you can directly download the compressed tar file and install it and play it.  

## PREREQUISITES
- No prerequisites
- May be More benefited Who are know Magento 2 Basic frontend , backend & install local/server .
- Fundamentals of Magento 2 Development or Module Development  as a first step.


## Goal:

- Develop Full-fledged Module Step by Step .
- Magento 2 Certified [Associate](mcad.md)/[Professional](mcpd.md) Developer exam Preparation hands-on practice.





## <a name="top"> Magento 2 SimpleNews Module Step By Step (BDCrops) </a>

##  [Part A : News Module for Basic](#PartA)


- [Step 2A.1: Create a directory for the module like above format](#Step2A1)
- [Step 2A.2: Declare module by using configuration file module.xml](#Step2A2)
- [Step 2A.3: Register module by registration.php & composer.json](#Step2A3)
- [Step 2A.4: Configure declarative schema (create table etc/db_schema.xml)](#Step2A4)
- [Step 2A.5: Schema whitelist (etc/db_schema_whitelist.json) ](#Step2A15)
- [Step 2A.6: Enable the module](#Step2A6)
- [Step 2A.7: Develop data and schema patches (Insert Installing and upgrading data)](#Step2A7)
- [Step 2A.8: Create Model News for business Logic](#Step2A8)
- [Step 2A.9: Create Model's ResourceModel to handle real database transaction](#Step2A9)
- [Step 2A.10: Create Model's collection class](#Step2A10)
- [Step 2A.11: Setup the frontend route](#Step2A11)
- [Step 2A.12: Create IndexController](#Step2A12)


### [Part B: News Module for Back End](#PartB)
- [Step 2B.1: Setup Module's backend configuration](#Step2B1)
- [Step 2B.2:  Create a custom source model](#Step2B2)
- [Step 2B.3:  Create a role for this config section](#Step2B3)
- [Step 2B.4:  Set some default value for configuration options](#Step2B4)
- [Step 2B.5:  Create a Helper Data class](#Step2B5)
- [Step 2B.6:  Create the menu for Magento backend](#Step2B6)
- [Step 2B.7:  Create backend route file](#Step2B7)
- [Step 2B.8:  Update the acl.xml to add more roles](#Step2B8)
- [Step 2B.9:  Create layout for grid](#Step2B9)
- [Step 2B.10:  Create layout for Grid Container](#Step2B10)
- [Step 2B.11:  Create layout for ajax load](#Step2B11)
- [Step 2B.12:  Create news status option file](#Step2B12)
- [Step 2B.13:  Create News Block for backend](#Step2B13)
- [Step 2B.14:  Create Grid block file for Ajax load](#Step2B14)
- [Step 2B.15:  Create a backend controller file for child action class to extend](#Step2B15)
- [Step 2B.16:  Create Backend Action file Index.php](#Step2B16)
- [Step 2B.17:  Create another Action for ajax](#Step2B17)
- [Step 2B.18:  Create layout file simplenews_news_edit.xml for edit form](#Step2B18)
- [Step 2B.19:  Create the layout for create form](#Step2B19)
- [Step 2B.20:  Create a form container block](#Step2B20)
- [Step 2B.21:  create a block for the left-side tabs](#Step2B21)
- [Step 2B.22:  Create a block for Form information](#Step2B22)
- [Step 2B.23:  Create a block to declare the fields for the edit form](#Step2B23)
- [Step 2B.24:  Create a controller action for create a new News](#Step2B24)
- [Step 2B.25:  Create Edit Action for the Edit form](#Step2B25)
- [Step 2B.26:  A Save Action for the edit form](#Step2B26)
- [Step 2B.27:  Delete Action for the edit Form](#Step2B27)
- [Step 2B.28:  The mass delete action the grid list](#Step2B28)
- [Step 2B.29:  Backend Menu and Grid List](#Step2B29)

## [Part C : News Module for Front End](#PartC)
- [Step 2C.1:  Create Layout file for page handle](#Step2C1)
- [Step 2C.2:  Create another layout file by update the previous layout](#Step2C2)
- [Step 2C.3:  Create Block NewList file](#Step2C3)
- [Step 2C.4:  Create frontend template file list.phtml](#Step2C4)
- [Step 2C.5:  Create an abstract class by extending Magento Core Action class](#Step2C5)
- [Step 2C.6:  Update Index Controller by extends the abstract class 'New.php'](#Step2C6)
- [Step 2C.7:  Create a layout file for news detail page](#Step2C7)
- [Step 2C.8:  Create News view action](#Step2C8)
- [Step 2C.9:  create view news block](#Step2C9)
- [Step 2C.10:  Create news view template file](#Step2C10)
- [Step 2C.11:  Create CSS file for styling the frontend Page](#Step2C11)
- [Step 2C.12:  Create Latest New Block](#Step2C12)
- [Step 2C.13:  Create a Block for positioning the latest news: Left or Right](#Step2C13)
- [Step 2C.14:  Create the template file for Latest News](#Step2C14)
- [Step 2C.15:  Frontend view for the module](#Step2C15)



##  <a name="PartA">Part A : News Module for Basic </a> [Go to Top](#top)

***

### <a name="Step2A1">Step 2A.1: Create a directory for the module like above format</a>

In this module, we will use `BDCrops` for Vendor name and `SimpleNews` for ModuleName. So we need to make this folder: `app/code/BDC/SimpleNews`

#### Notes[u can skip]:

##### Magento 2  Model View ViewModel (MVVM) Architecture
- Model: Holds business logic of  application & depends on an associated class—the ResourceModel—for database access. Models rely on service contracts to expose their functionality to  other layers of  application.
- View: Structure & layout of what a user sees on a screen - the actual HTML. This is achieved in the PHTML files distributed with modules. PHTML files are associated to each ViewModel in the Layout XML files, which would be referred to as binders in the MVVM dialect. The layout files might also assign JavaScript files to be used in the final page.
- ViewModel: Interacts with  Model layer, exposing only  necessary information to  View layer handled by the module’s Block classes. Note that this was usually part of the Controller role of an MVC system. On MVVM, the controller is only responsible for handling the user flow, meaning that it receives requests and either tells the system to render a view or to redirect the user to another route.

##### Module  folder holds one part of the architecture, as follows:

- Api or Api/Data: Service contracts, defining service interfaces & data interfaces
- Adapter:Classes follow  adapter pattern & wrap around classes from third-party libraries allow  to use functionality from third-party libraries in  code by converting the third-party class interfaces into an interface that is expected by  native code.( module-search/Adapter/)
- Block:  ViewModels of our MVVM architecture
- Collector: module-deploy/Collector/Collector.php
- Command: directory is used for storing the PHP files that are responsible for console programs execution. In our case, Console/Command/ImagesResizeCommand.php processes commands for product images resizing.
- Controller: Responsible for handling the user’s flow while interacting with the system
- Config: module-deploy/Config/BundleConfig.php
- Cron: We use the directory to store the files, which are later executed on the Cron launching.
- CustomerData: directory contains PHP files responsible for processing information for sections. Magento 2 has a special functionality, which allows for processing, updating and transferring the information asynchronously.
- etc: Configuration XML files—The module defines itself and its parts (routes, models, blocks, observers, and cron jobs) within this folder. The etc files can also be used by non-core modules to override the functionality of core modules.
- Exception: (module-sales/Exception/)
- Files: Sample file  (module-inventory-import-export/Files/)
- fixtures: Sample Data module (module-sales-sample-data/fixtures/orders.csv)
- Gateway: (module-paypal/Gateway)
- Helper: Classes that hold code used in more than one application layer. For example, in the Cms module, helper classes are responsible for preparing HTML for presentation to the browser.
- i18n: Holds internationalization CSV files, used for translation
- Indexer: IndexHandler  (module-inventory-indexer/Indexer)
- Model: For Models and ResourceModels
- Observer: Holds Observers, or Models which are “observing” system events. Usually, when such an event is fired, the observer instantiates a Model to handle the necessary business logic for such an event.
- Package: module-deploy/Package
- Pricing: Final price model  (module-msrp-grouped-product/Pricing)
- Process: module-deploy/Process
- Plugin: directory comprises plugin files  allow us to modify certain module’s functions if necessary described in the configuration file: vendor/magento/module-catalog/etc/di.xml
- SearchAdapter: module-elasticsearch/SearchAdapter
- ReportXml :vendor/magento/module-analytics/ReportXml
- Setup: Migration classes, responsible for schema & data creation
- Service: [exam] (module-media-storage/Service/ImageResize.php,module-deploy/ or module-catalog-url-rewrite/Service/V1/StoreViewService.php )
- src : vendor/magento/magento2-functional-testing-framework/src/Magento/
- Strategy: module-deploy/Strategy
- Source: module-deploy/Source
- Test: Unit tests
- Ui: Elements such as grids & forms used in  admin application
- view: Layout (XML) files & template (PHTML) files for  front-end & admin application
- ViewModel: (module-sales/ViewModel)

### <a name="Step2A2">Step 2A.2: Declare module by using configuration file module.xml</a>

Magento 2 looks for configuration information for each module in that module’s etc directory. We need to create folder etc and add module.xml:
 Create app/code/BDC/SimpleNews/etc/module.xml And the content for this file:

~~~ xml
<?xml version="1.0"?>
<config xmlns:xsi="http://www.w3.org/2001/XMLSchema-instance" xsi:noNamespaceSchemaLocation="urn:magento:framework:Module/etc/module.xsd">
    <module name="BDC_SimpleNews" setup_version="1.0.0" />
</config>
~~~
In this file, we register a module with name `BDC_SimpleNews` and the version is `1.0.0`.

#### Notes[u can skip]:
- Magento 2 need  Two Mandatory File to  run/activate Module etc/module.xml & registration.php

### <a name="Step2A3"> Step 2A.3: Register module by registration.php</a>

All Magento 2 module must be registered in the Magento system through the magento ComponentRegistrar class. This file will be placed in module root directory.
In this step, we need to create this file:
Create  app/code/BDC/SimpleNews/registration.php and insert this following code into it:

~~~
\Magento\Framework\Component\ComponentRegistrar::register(
    \Magento\Framework\Component\ComponentRegistrar::MODULE,
    'BDC_SimpleNews',
    __DIR__
);
~~~

Modules in vendor folder would update using composer And all the modules in app/code would not be updated through composer That's why when you need to override any module you add it in app/code

Create  app/code/BDC/SimpleNews/composer.json  and insert this following code into it:

```
{
    "name": "bdc/module-simplenews",
    "description": "BDCrops SimpleNews module for Magento 2 extensions.",
    "type": "magento2-module",
    "version": "1.0.0",
    "license": [
        "OSL-3.0",
        "AFL-3.0"
    ],
	"authors": [{
            "name": "Abdul Matin",
            "email": "matinict@gmail.com",
			      "company": "BDCrops Inc"
        }
    ],
	"homepage": "https://www.bdcrops.com",
    "autoload": {
        "files": [
            "registration.php"
        ],
        "psr-4": {
            "BDC\\SimpleNews\\": ""
        }
    }
}

```


### <a name="Step2A4">Step 2A.4: Configure declarative schema (create table  schema Installation file)</a>

Create  app/code/BDC/SimpleNews/etc/db_schema.xml &  insert this following code into it:

```
<?xml version="1.0"?>
<schema xmlns:xsi="http://www.w3.org/2001/XMLSchema-instance" xsi:noNamespaceSchemaLocation="urn:magento:framework:Setup/Declaration/Schema/etc/schema.xsd">

  <table name="bdc_simplenews" resource="default" engine="innodb" comment="SimpleNews Table">
        <column xsi:type="smallint" name="id" padding="6" unsigned="false" nullable="false" identity="true" comment="ID"/>
        <column xsi:type="varchar" name="title" nullable="false" length="255" comment="Title"/>
        <column xsi:type="varchar" name="summary" nullable="false" length="255" comment="Summary"/>
        <column xsi:type="varchar" name="description" nullable="false" length="255" comment="Descrition"/>
        <column xsi:type="timestamp" name="created_at" nullable="false" default="CURRENT_TIMESTAMP" on_update="false" comment="Created Datetime"/>
        <column xsi:type="timestamp" name="updated_at" nullable="false" default="CURRENT_TIMESTAMP" on_update="true" comment="Updated Datetime"/>
        <column xsi:type="smallint" name="status"  padding="2" unsigned="false" nullable="false" comment="Status"/>
        <constraint xsi:type="primary" referenceId="PRIMARY">   <column name="id"/> </constraint>
    </table>
</schema>
```
#### Note:

### <a name="Step2A5">Step 2A.5: Schema whitelist (etc/db_schema_whitelist.json) </a>

You will not be able to run a declarative mode without creating a schema whitelist.
Note: it is recommended to generate a new whitelist for every release for the double-check purposes.

Before running the upgrade command you need to add your schema to db_whitelist_schema.json file by running the following command.

For that, you need a /etc/db_schema_whitelist.json file that will store all the content added with declarative schema. To generate this file, run:


![db_schema](https://github.com/bdcrops/BDC_Declarative/blob/master/view/adminhtml/web/images/whitelist.png)


php bin/magento setup:db-declaration:generate-whitelist [options]
php bin/magento setup:db-declaration:generate-whitelist --module-name=vendor_module

php bin/magento setup:db-declaration:generate-whitelist --module-name=BDC_SimpleNews


Now, there are db_whitelist_schema.json file will be create in /vendor/module/etc folder.
![db_whitelist_schema](https://github.com/bdcrops/BDC_SimpleNews/blob/master/doc/db_schema_whitelist.png)



### <a name="Step2A6">Step 2A.6: Enable the module</a>


By finish above step, you have created an empty module. Now we will enable it in Magento environment.
Before enable the module, we must check to make sure Magento has recognize our module or not by enter the following at the command line:

~~~
php bin/magento module:status
~~~

If you follow above step, you will see this in the result:

~~~
List of disabled modules:
BDC_SimpleNews
~~~

This means the module has recognized by the system but it is still disabled. Run this command to enable it:

~~~
php bin/magento module:enable BDC_SimpleNews
~~~

The module has enabled successfully if you saw this result:

~~~
The following modules has been enabled:
- BDC_SimpleNews
~~~

This’s the first time you enable this module so Magento require to check and upgrade module database. We need to run this comment:

~~~
php bin/magento setup:upgrade
~~~

Now you can check under `Stores -> Configuration -> Advanced -> Advanced` that the module is present.

Also  you can check Database Table from PhpMyAdmin or Your Favorite tools:

![Table db_schema](https://github.com/bdcrops/BDC_SimpleNews/blob/master/doc/dbTableCreatedDeclarativeSchema.png)



### <a name="Step2A7">Step 2A.7:  Develop data and schema patches (Insert data Installing and upgrading data)</a>


Since in the old method, we used to write scripts in Install Schema or Upgrade schema when a table was created, but now in the new version, this will be done through Patch system.

A data patch is a class that contains data modification instructions. It is defined in a <Namespace>/<Module_Name>/Setup/Patch/Data/<Patch_Name>.php file and implements \Magento\Setup\Model\Patch\DataPatchInterface.

A schema patch contains custom schema modification instructions. These modifications can be complex.

It is defined in a<Vendor>/<Module_Name>/Setup/Patch/Schema/<Patch_Name>.php file and implements \Magento\Setup\Model\Patch\SchemaPatchInterface.


So to add data to the bdc_simplenews table create AddData.php file inside folder BDC/SimpleNews/Setup/Patch/Data and write the following code

app/code/BDC/SimpleNews/Setup/Patch/Data/AddData.php

```
<?php

namespace BDC\SimpleNews\Setup\Patch\Data;

use Magento\Framework\Setup\Patch\DataPatchInterface;
use Magento\Framework\Setup\Patch\PatchVersionInterface;
use Magento\Framework\Module\Setup\Migration;
use Magento\Framework\Setup\ModuleDataSetupInterface;

class AddData implements DataPatchInterface, PatchVersionInterface {
    private $news;
    public function __construct( \BDC\SimpleNews\Model\News $news ) {
        $this->news = $news;
    }
    public function apply(){
    	$newsData = [];
    	$newsData['title'] = "BDC News Head1";
    	$newsData['summary'] = "BDC News Summary";
    	$newsData['description'] = "BDCrops Inc description evulation of bangladesh";
    	//$newsData['status'] = 1;

    	$this->news->addData($newsData);
    	$this->news->getResource()->save($this->news);

    }
    public static function getDependencies() {   return []; }
    public static function getVersion() { return '2.0.0'; }
    public function getAliases() {   return []; }

}


```

### <a name="Step2A8"> Step 2A.8: Create Model News for business Logic</a>

We need to create these files to insert, update, delete and get data in the database.

- Create model file: app/code/BDC/SimpleNews/Model/News.php and insert this following code into it:
```
<?php
// These files to insert, update, delete and get data in the database.
namespace BDC\SimpleNews\Model;
use Magento\Framework\Model\AbstractModel;

class News extends AbstractModel{
    /**
     * News constructor.
     * @param \Magento\Framework\Model\Context $context
     * @param \Magento\Framework\Registry $registry
     * @param \Magento\Framework\Model\ResourceModel\AbstractResource|null $resource
     * @param \Magento\Framework\Data\Collection\AbstractDb|null $resourceCollection
     * @param array $data
     */
    public function __construct(
        \Magento\Framework\Model\Context $context,
        \Magento\Framework\Registry $registry,
        \Magento\Framework\Model\ResourceModel\AbstractResource $resource = null,
        \Magento\Framework\Data\Collection\AbstractDb $resourceCollection = null,
        array $data = []
    ) {
        parent::__construct($context, $registry, $resource, $resourceCollection, $data);
    }

   /**
    * (non-PHPdoc)
    * @see \Magento\Framework\Model\AbstractModel::_construct()
    */
    public function _construct()
    {
        $this->_init('BDC\SimpleNews\Model\Resource\News');
    }

    /**
     * Loading news data
     *
     * @param   mixed $key
     * @param   string $field
     * @return  $this
     */
    public function load($key, $field = null) {
    	if ($field === null) {
    		$this->_getResource()->load($this, $key, 'id');
    		return $this;
    	}
    	$this->_getResource()->load($this, $key, $field);
    	return $this;
    }
}

```
#### <a name="Step2A8Note1"> Note: basic concepts of models, resource models, and collections</a>
CRUD Models in Magento 2 can manage data in database easily, you don’t need to write many line of code to create a CRUD. CRUD is stand for Create, Read, Update and Delete.
The Magento ORM is used by the Repository implementations that are part of the Magento 2 service contracts. This is an important variation from Magento 1, as a module should no longer rely on other modules using a specific ORM, and instead of it use only the entity repositories. The service contracts will be covered in more details in the second part of the article.The Magento ORM is built around models, resource models, and resource collections. The Magento ORM elements are following:

-  Models are data and behavior, representing entities.
- Resource Models are data mappers for the storage structure.
- Collections are encapsulating sets of models and related functionality, such as filtering, sorting, and paging.
- Resources include database connections via adapters.
#### <a name="Step2A8Note2">Note:native Magento save/load </a>
The ORM gives you a possibility to create, load, update, and delete data in a database. A collection in Magento is a class that implements both the IteratorAggregate and the Countable PHP5 SPL interfaces. Collections are widely used in Magento to store a set of objects of a specific type.

#### <a name="Step2A8Note3">NOte: Models</a>
Models are like a black box which provides a layer of abstraction on top of the resource models. The fetching, extraction, and manipulation of data occur through models. As a rule of thumb, every entity we create (i.e. every table we create in our database) should have its own model class. Every model extends the Magento\Framework\Model\AbstractModelclass, which inherits the \Magento\Framework\DataObjectclass, hence, we can call the setDataand getData functions on our model, to get or set the data of a model respectively. class only has one method, _ construct(), when we call the _ init()method, and pass the resource model’s name as its paramete


### <a name="Step2A9">Step 2A.9: Create Model's ResourceModel to handle real database transaction</a>

- Create resource model file: app/code/BDC/SimpleNews/Model/Resource/News.php and insert this following code into it:
```
<?php

namespace BDC\SimpleNews\Model\Resource;

use Magento\Framework\Model\ResourceModel\Db\AbstractDb;

class News extends AbstractDb {
    /**
     * Define main table
     */
    protected function _construct()
    {
        $this->_init('bdc_simplenews', 'id');
    }
}

```

#### <a name="Step2A9Note1">Note: Resource Model</a>
All of the actual database operations are executed by the resource model. Every model must have a resource model, since all of the methods of a resource model expects a model as its first parameter. All resource models must extend the Magento\Framework\Model\ResourceModel\Db\AbstractDbclass.
here also has one method, <__ construct>, where we call the <_ initmethod>, and pass two parameters to it. The name of the table in the database, and the name of the primary column in that table.
Resource Model. In Magento 2, the model class defines the methods an end-user-programmer will use to interact with a model’s data. A resource model class contains the methods that will actually fetch the information from the database. Each CRUD model in Magento 2 has a corresponding resource model class.

Every CRUD resource model class extends the Magento\Framework\Model\ResourceModel\Db\AbstractDb class. This base class contains the basic logic for fetching information from a single database table.
For a basic model like ours, the only thing a resource model must do is call the _ init method from _ construct. The _ init method for a resource model accepts two arguments. The first is the name of the database table (pulsestorm_todocrud_todoitem), and the second is the ID column for the model (pulsestorm_todocrud_todoitem_id). While it’s beyond the scope of this article, Magento 2’s active record implementation contains no method for linking tables via primary keys. How to use multiple database tables is up to each individual module developer, and a resource model will typically contain the SQL generating methods needed to fetch information from related tables.


### <a name="Step2A10">Step 2A.10: Create Model's collection class</a>

- Create collection file: app/code/BDC/SimpleNews/Model/Resource/News/Collection.php and insert this following code into it:

```
<?php
namespace BDC\SimpleNews\Model\Resource\News;

use Magento\Framework\Model\ResourceModel\Db\Collection\AbstractCollection;
class Collection extends AbstractCollection {
    /**
     * Define model & resource model
     */
    protected function _construct(){
        $this->_init(
            'BDC\SimpleNews\Model\News',
            'BDC\SimpleNews\Model\Resource\News'
        );
    }
}

```
#### <a name="Step2A10Note1">Note:  Collection </a>
Collections are used when we want to fetch multiple rows from our table. Meaning collections
- group of models. Collections can be used when we want to
- Fetch multiple rows from a table
- Join tables with our primary table
- Select specific columns
- Apply a WHERE clause to our query
- Use GROUP BY or ORDER BY in our query

With a model and resource model, you have everything you need to fetch and save individual models into the database. However, there are times where you’ll want to fetch multiple models of a particular type. To solve this problem, every CRUD model in Magento 2 has a corresponding resource model collection. A collection collects individual models. It’s considered a resource model since it builds the SQL code necessary to pull information from a database table.
All collections in Magento 2 extend the base \Magento\Framework\Model\ResourceModel\Db\Collection\AbstractCollection collection class. Like a model and resource model, a collection resource model must call the _ init method. A collection resource model’s _ init method accepts two arguments. The first is the model that this collection collects. The second is that collected model’s resource model.
We create a new Magento 2 block an inject \Magento\Catalog\Model\ResourceModel\Product\CollectionFactory class. This is needed to get a collection from factory. A getProductCollection returns a new product collection. This method does the following:

- create a new collection from collection factory
- filter attributes (collumns)
- This time we want to load all data (* ), you can also add a comma seperated list of attribute names. Only this attributes get loaded – lazy loading optimizes your database select statement.
- filter by attribute values
It is possible to filter your collection by loaded attribute values. For example all products with price small than 1000 $. My example use setPageSize() to only load a given number of products.

### <a name="Step2A11">Step 2A.11: Setup the frontend route</a>

In the Magento system, a request URL has the following format:

~~~
http://example.com/<router_name>/<controller_name>/<action_name>
~~~

The Router is used to assign a URL to a corresponding controller and action. In this module, we need to create a route for frontend area. So we need to add this file:

Create  app/code/BDC/SimpleNews/etc/frontend/routes.xml and insert this following code into it:


~~~
<?xml version="1.0"?>
<config xmlns:xsi="http://www.w3.org/2001/XMLSchema-instance"
xsi:noNamespaceSchemaLocation="../../../../../../lib/internal/Magento/Framework/
App/etc/routes.xsd">
    <router id="standard">
        <route id="bdcnews" frontName="news">
            <module name="BDC_SimpleNews" />
        </route>
    </router>
</config>
~~~

After define the route, the URL path to our module will be: `http://example.com/news/`

#### <a name="Step2A11Note1">Note: Controllers, Routers and Responses</a>
- Routers: define name for a module which we can use in the url to find the module and execute the controller action.
- Controllers:Controllers in Magento 2 differ from typical controllers in MVC applications. Magento 2 controllers are responsible for only one specific URL and contain only one execute method. This method is responsible for returning result object and occasional processing of input POST data. All controllers inherit \Magento\Framework\App\Action\Action class. The required controller is searched in the Base Router, and then it’s called in the Front Controller.
- Responses: The controller in Magento 2 can return several response types depending on the purpose and the necessary result.


### <a name="Step2A12">Step 2A.12: Create IndexController</a>


- Create controller file: app/code/BDC/SimpleNews/Controller/Index/Index.php and insert this following code into it:

```
<?php

namespace BDC\SimpleNews\Controller\Index;

use Magento\Framework\App\Action\Action;
use Magento\Framework\App\Action\Context;
use BDC\SimpleNews\Model\NewsFactory;

class Index extends Action {
    /**
     * @var \BDC\SimpleNews\Model\NewsFactory
     */
    protected $_modelNewsFactory;
    /**
     * @param Context $context
     * @param NewsFactory $modelNewsFactory
     */
    public function __construct(
        Context $context,
        NewsFactory $modelNewsFactory ) {
        parent::__construct($context);
        $this->_modelNewsFactory = $modelNewsFactory;
    }
    public function execute(){
        /**
         * When Magento get your model, it will generate a Factory class
         * for your model at var/generaton folder and we can get your
         * model by this way
         */
        $newsModel = $this->_modelNewsFactory->create();

        // Load the item with ID is 1
        $item = $newsModel->load(1);
        var_dump($item->getData());

        // Get news collection
        $newsCollection = $newsModel->getCollection();
        // Load all data of collection
        var_dump($newsCollection->getData());
    }
}

```
After define the Controller, the URL path to our module will be: `http://example.com/news/` below data

![NewsDataFrontend](https://github.com/bdcrops/BDC_SimpleNews/blob/master/doc/newsFrontendData.png)



#### <a name="Step2A12Note1"> Responses: create a frontend controller with different response types</a>
- Page Result (\Magento\Framework\View\Result\Page) is the most common type of response. By returning this object, the controller starts the standard page rendering based on the corresponding XML layout handle.
```
public function __construct(
   $pageFactory Magento\Framework\View\Result\PageFactory
) {
   $this->pageResultFactory = $pageFactory
}
public function execute()
{
   return $this->pageResultFactory->create();
}
```
- Raw Result (\Magento\Framework\Controller\Result\Raw) is used if you want to return a string to the browser without using Magento layout and view rendering.
```
public function __construct(
   Magento\Framework\Controller\Result\Raw $rawResultFactory ,
) {
   $this->rawResultFactory = $rawResultFactory;
}
public function execute()
{
   $result = $this->rawResultFactory->create();
   $result->setHeader('Content-Type', 'text/xml');
   $result->setContents('<root><block></block></root>);
   return $result;
}
```

- Forward Result (\Magento\Framework\Controller\Result\Forward) allows to call another method/controller without changing the URL or redirecting.
```
public function __construct(
   Magento\Framework\Controller\Result\Forward\Factory $resultForwardFactory    
) {
   $this->resultForwardFactory = $resultForwardFactory;
}
public function execute()
{
   $result = $this->resultForwardFactory->create();
   $result->forward('noroute');    
   return $result;
}
```
- Redirect Result (\Magento\Framework\Controller\Result\Redirect) is used when a user needs to be redirected to a different URL.
```
public function __construct(
   Magento\Framework\Controller\Result\Redirect\Factory $resultRedirectFactory
) {
   $this->resultRedirectFactory = $resultRedirectFactory;
}
public function execute()
{
   $result = $this->resultRedirectFactory->create();
   $result->setPath('*/*/index');
   return $result;
}
```



### <a name="PartB">Part B: News Module for Back End </a>   [Go to Top](#top)
***


### <a name="Step2B1">Step 2B.1: Setup Module's backend configuration</a>

- Create file: app/code/BDC/SimpleNews/etc/adminhtml/system.xml (Purpose: This file will declare your configurations in Stores > Settings > Configuration section) and insert this following code into it:

```
<?xml version="1.0"?>

<config xmlns:xsi="http://www.w3.org/2001/XMLSchema-instance" xsi:noNamespaceSchemaLocation="../../../Backend/etc/system_file.xsd">
    <system>
        <tab id="bdc" translate="label" sortOrder="1">
            <label>BDC</label>
        </tab>
        <section id="simplenews" translate="label" sortOrder="1" showInDefault="1" showInWebsite="1" showInStore="1">
            <label>Simple News</label>
            <tab>bdc</tab>
            <resource>BDC_SimpleNews::system_config</resource>
            <group id="general" translate="label" type="text" sortOrder="1" showInDefault="1" showInWebsite="1" showInStore="1">
                <label>General Settings</label>
                <field id="enable_in_frontend" translate="label" type="select" sortOrder="1" showInDefault="1" showInWebsite="1" showInStore="1">
                    <label>Enable in frontend</label>
                    <source_model>Magento\Config\Model\Config\Source\Yesno</source_model>
                </field>
                <field id="head_title" translate="label comment" type="text" sortOrder="2" showInDefault="1" showInWebsite="1" showInStore="1">
                    <label>Head title</label>
                    <comment>Fill head title of news list page at here</comment>
                    <validate>required-entry</validate>
                </field>
                <field id="lastest_news_block_position" translate="label" type="select" sortOrder="3" showInDefault="1" showInWebsite="1" showInStore="1">
                    <label>Lastest news block position</label>
                    <source_model>BDC\SimpleNews\Model\System\Config\LastestNews\Position</source_model>
                </field>
            </group>
        </section>
    </system>
</config>

```

### <a name="Step2B2">Step 2B.2:  Create a custom source model</a>

- Create file: app/code/BDC/SimpleNews/Model/System/Config/LastestNews/Position.php and insert this following code into it:

```
<?php

namespace BDC\SimpleNews\Model\System\Config\LastestNews;

use Magento\Framework\Option\ArrayInterface;

class Position implements ArrayInterface{
    const LEFT      = 1;
    const RIGHT     = 2;
    const DISABLED  = 0;

    /**
     * Get positions of lastest news block
     *
     * @return array
     */
    public function toOptionArray(){
        return [
            self::LEFT => __('Left'),
            self::RIGHT => __('Right'),
            self::DISABLED => __('Disabled')
        ];
    }
}

```

### <a name="Step2B3">Step 2B.3:  Create a role for this config section</a>

- Create file: app/code/BDC/SimpleNews/etc/acl.xml (Purpose: This file will create a role for your configuration section) and insert this following code into it:

```
<?xml version="1.0"?>

<config xmlns:xsi="http://www.w3.org/2001/XMLSchema-instance"
xsi:noNamespaceSchemaLocation="../../../../../lib/internal/Magento/Framework/Acl/etc/acl.xsd">
    <acl>
        <resources>
            <resource id="Magento_Backend::admin">
                <resource id="Magento_Backend::stores">
                    <resource id="Magento_Backend::stores_settings">
                        <resource id="Magento_Config::config">
                            <resource id="BDC_SimpleNews::system_config" title="Simple News Section" />
                        </resource>
                    </resource>
                </resource>
            </resource>
        </resources>
    </acl>
</config>


```

### <a name="Step2B4">Step 2B.4:  Set some default value for configuration options</a>

- Create file: app/code/BDC/SimpleNews/etc/config.xml and insert this following code into it:
```
<?xml version="1.0"?>
<config xmlns:xsi="http://www.w3.org/2001/XMLSchema-instance"
xsi:noNamespaceSchemaLocation="../../Core/etc/config.xsd">
    <default>
        <simplenews>
            <general>
                <enable_in_frontend>1</enable_in_frontend>
                <head_title>BDC - Simple News</head_title>
                <lastest_news_position>1</lastest_news_position>
            </general>
        </simplenews>
    </default>
</config>

```


### <a name="Step2B5">Step 2B.5:  Create a Helper Data class</a>

- Create file: app/code/BDC/SimpleNews/Helper/Data.php and insert this following code into it:

```
<?php

namespace BDC\SimpleNews\Helper;

use Magento\Framework\App\Helper\AbstractHelper;
use Magento\Framework\App\Config\ScopeConfigInterface;
use Magento\Framework\App\Helper\Context;
use Magento\Store\Model\ScopeInterface;

class Data extends AbstractHelper {
   const XML_PATH_ENABLED      = 'simplenews/general/enable_in_frontend';
   const XML_PATH_HEAD_TITLE   = 'simplenews/general/head_title';
   const XML_PATH_LASTEST_NEWS = 'simplenews/general/lastest_news_block_position';

   /**
     * @var \Magento\Framework\App\Config\ScopeConfigInterface
     */
    protected $_scopeConfig;

    /**
     * @param Context $context
     * @param ScopeConfigInterface $scopeConfig
     */
    public function __construct(
       Context $context,
       ScopeConfigInterface $scopeConfig ) {
       parent::__construct($context);
       $this->_scopeConfig = $scopeConfig;
    }

   /**
     * Check for module is enabled in frontend
     *
     * @return bool
     */
   public function isEnabledInFrontend($store = null)
   {
      return $this->_scopeConfig->getValue(
         self::XML_PATH_ENABLED,
         ScopeInterface::SCOPE_STORE
      );
   }

   /**
     * Get head title for news list page
     *
     * @return string
     */
   public function getHeadTitle()
   {
      return $this->_scopeConfig->getValue(
         self::XML_PATH_HEAD_TITLE,
         ScopeInterface::SCOPE_STORE
      );
   }

   /**
     * Get lastest news block position (Left, Right, Disabled)
     *
     * @return int
     */
   public function getLastestNewsBlockPosition()
   {
      return $this->_scopeConfig->getValue(
         self::XML_PATH_LASTEST_NEWS,
         ScopeInterface::SCOPE_STORE
      );
   }
}

```



### <a name="Step2B6">Step 2B.6:  Create the menu for Magento backend</a>

Create file: app/code/BDC/SimpleNews/etc/adminhtml/menu.xml (Purpose: The menu item of your module will be declared here) and insert this following code into it:

```
<?xml version="1.0"?>

<config xmlns:xsi="http://www.w3.org/2001/XMLSchema-instance"
xsi:noNamespaceSchemaLocation="../../../Backend/etc/menu.xsd">
    <menu>
        <add id="BDC_SimpleNews::main_menu" title="Simple News"
            module="BDC_SimpleNews" sortOrder="20"
            resource="BDC_SimpleNews::simplenews" />
        <add id="BDC_SimpleNews::add_news" title="Add News"
            module="BDC_SimpleNews" sortOrder="1" parent="BDC_SimpleNews::main_menu"
            action="simplenews/news/new" resource="BDC_SimpleNews::manage_news" />
        <add id="BDC_SimpleNews::manage_news" title="Manage News"
            module="BDC_SimpleNews" sortOrder="2" parent="BDC_SimpleNews::main_menu"
            action="simplenews/news/index" resource="BDC_SimpleNews::manage_news" />
        <add id="BDC_SimpleNews::configuration" title="Configurations"
            module="BDC_SimpleNews" sortOrder="3" parent="BDC_SimpleNews::main_menu"
            action="adminhtml/system_config/edit/section/simplenews"
            resource="BDC_SimpleNews::configuration" />
    </menu>
</config>

```

![MenuLinkAdmin](https://github.com/bdcrops/BDC_SimpleNews/blob/master/doc/adminhtmlMenu.png)


### <a name="Step2B7">Step 2B.7:  Create backend route file</a>

- Create file: app/code/BDC/SimpleNews/etc/adminhtml/routes.xml (Purpose: The router of your module for backend will be declared here) and insert this following code into it:

```
<?xml version="1.0"?>

<config xmlns:xsi="http://www.w3.org/2001/XMLSchema-instance"
xsi:noNamespaceSchemaLocation="../../../../../../lib/internal/Magento/
Framework/App/etc/routes.xsd">
    <router id="admin">
        <route id="simplenews" frontName="simplenews">
            <module name="BDC_SimpleNews" />
        </route>
    </router>
</config>

```

### <a name="Step2B8">Step 2B.8:  Update the acl.xml to add more roles</a>

- Open this file: app/code/BDC/SimpleNews/etc/acl.xml and modify the source code into here like this:
```
<?xml version="1.0"?>

<config xmlns:xsi="http://www.w3.org/2001/XMLSchema-instance" xsi:noNamespaceSchemaLocation="../../../../../lib/internal/Magento/
Framework/Acl/etc/acl.xsd">
    <acl>
        <resources>
            <resource id="Magento_Backend::admin">
                <resource id="BDC_SimpleNews::simplenews" title="Simple News" sortOrder="100">
                    <resource id="BDC_SimpleNews::add_news" title="Add News" sortOrder="1" />
                    <resource id="BDC_SimpleNews::manage_news" title="Manage News" sortOrder="2" />
                    <resource id="BDC_SimpleNews::configuration" title="Configurations" sortOrder="3" />
                </resource>
                <resource id="Magento_Backend::stores">
                    <resource id="Magento_Backend::stores_settings">
                        <resource id="Magento_Config::config">
                            <resource id="BDC_SimpleNews::system_config" title="Simple News Section" />
                        </resource>
                    </resource>
                </resource>
            </resource>
        </resources>
    </acl>
</config>

```

### <a name="Step2B9">Step 2B.9:  Create layout for grid</a>


- Create file: app/code/BDC/SimpleNews/view/adminhtml/layout/simplenews_news_index.xml (Purpose: This file is used to declare grid container block) and insert this following code into it:

```
<?xml version="1.0"?>

<page xmlns:xsi="http://www.w3.org/2001/XMLSchema-instance" xsi:noNamespaceSchemaLocation="../../../../../../../lib/internal/Magento/Framework/View/Layout/etc/page_configuration.xsd">
   <update handle="formkey"/>
   <update handle="simplenews_news_grid_block"/>
   <body>
       <referenceContainer name="content">
           <block class="BDC\SimpleNews\Block\Adminhtml\News"
               name="bdc_simplenews_news.grid.container" />
       </referenceContainer>
   </body>
</page>

```

### <a name="Step2B10">Step 2B.10:  Create layout for Grid Container</a>


- Create file: app/code/BDC/SimpleNews/view/adminhtml/layout/simplenews_news_grid_block.xml (Purpose: This file is used to declare the content of grid block) and insert this following code into it:

```
<?xml version="1.0"?>

<page xmlns:xsi="http://www.w3.org/2001/XMLSchema-instance" xsi:noNamespaceSchemaLocation="../../../../../../../lib/internal/Magento/Framework/View/Layout/etc/page_configuration.xsd">
    <body>
      <referenceBlock name="bdc_simplenews_news.grid.container">
         <block class="Magento\Backend\Block\Widget\Grid" name="bdc_simplenews_news.grid"
             as="grid">
             <arguments>
                 <argument name="id" xsi:type="string">newsGrid</argument>
                 <argument name="dataSource" xsi:type="object">BDC\SimpleNews\Model\Resource\News\Collection</argument>
                 <argument name="default_sort" xsi:type="string">id</argument>
                 <argument name="default_dir" xsi:type="string">desc</argument>
                 <argument name="save_parameters_in_session" xsi:type="boolean">true</argument>
                 <argument name="use_ajax" xsi:type="boolean">true</argument>
                 <argument name="grid_url" xsi:type="url" path="*/*/grid">
                     <param name="_current">1</param>
                 </argument>
             </arguments>
                <block class="Magento\Backend\Block\Widget\Grid\Massaction"
                    name="bdc_simplenews_news.grid.massaction" as="grid.massaction">
                    <arguments>
                        <argument name="massaction_id_field" xsi:type="string">id</argument>
                        <argument name="form_field_name" xsi:type="string">news</argument>
                        <argument name="options" xsi:type="array">
                            <item name="delete" xsi:type="array">
                                <item name="label" xsi:type="string" translate="true">Delete</item>
                                <item name="url" xsi:type="string">*/*/massDelete</item>
                                <item name="confirm" xsi:type="string" translate="true">Are you sure you want to delete?</item>
                            </item>
                        </argument>
                    </arguments>
                </block>
                <block class="Magento\Backend\Block\Widget\Grid\ColumnSet"
                    name="bdc_simplenews_news.grid.columnSet" as="grid.columnSet">
                    <arguments>
                        <argument name="rowUrl" xsi:type="array">
                            <item name="path" xsi:type="string">*/*/edit</item>
                            <item name="extraParamsTemplate" xsi:type="array">
                                <item name="id" xsi:type="string">getId</item>
                            </item>
                        </argument>
                    </arguments>
                    <block class="Magento\Backend\Block\Widget\Grid\Column" as="id">
                        <arguments>
                            <argument name="header" xsi:type="string" translate="true">ID</argument>
                            <argument name="type" xsi:type="string">number</argument>
                            <argument name="id" xsi:type="string">id</argument>
                            <argument name="index" xsi:type="string">id</argument>
                        </arguments>
                    </block>
                    <block class="Magento\Backend\Block\Widget\Grid\Column" as="title">
                        <arguments>
                            <argument name="header" xsi:type="string" translate="true">Title</argument>
                            <argument name="index" xsi:type="string">title</argument>
                        </arguments>
                    </block>
                    <block class="Magento\Backend\Block\Widget\Grid\Column" as="summary">
                        <arguments>
                            <argument name="header" xsi:type="string" translate="true">Summary</argument>
                            <argument name="index" xsi:type="string">summary</argument>
                        </arguments>
                    </block>
                    <block class="Magento\Backend\Block\Widget\Grid\Column" as="status">
                        <arguments>
                            <argument name="header" xsi:type="string" translate="true">Status</argument>
                            <argument name="index" xsi:type="string">status</argument>
                            <argument name="type" xsi:type="string">options</argument>
                            <argument name="options" xsi:type="options" model="BDC\SimpleNews\Model\System\Config\Status"/>
                        </arguments>
                    </block>
                    <block class="Magento\Backend\Block\Widget\Grid\Column" as="action" acl="BDC_SimpleNews::manage_news">
                        <arguments>
                            <argument name="id" xsi:type="string">action</argument>
                            <argument name="header" xsi:type="string" translate="true">Action</argument>
                            <argument name="type" xsi:type="string">action</argument>
                            <argument name="getter" xsi:type="string">getId</argument>
                            <argument name="filter" xsi:type="boolean">false</argument>
                            <argument name="sortable" xsi:type="boolean">false</argument>
                            <argument name="index" xsi:type="string">stores</argument>
                            <argument name="is_system" xsi:type="boolean">true</argument>
                            <argument name="actions" xsi:type="array">
                                <item name="view_action" xsi:type="array">
                                    <item name="caption" xsi:type="string" translate="true">Edit</item>
                                    <item name="url" xsi:type="array">
                                        <item name="base" xsi:type="string">*/*/edit</item>
                                    </item>
                                    <item name="field" xsi:type="string">id</item>
                                </item>
                            </argument>
                            <argument name="header_css_class" xsi:type="string">col-actions</argument>
                            <argument name="column_css_class" xsi:type="string">col-actions</argument>
                        </arguments>
                    </block>
                </block>
         </block>
      </referenceBlock>
    </body>
</page>

```


### <a name="Step2B11">Step 2B.11:  Create layout for ajax load</a>

- Create file: app/code/BDC/SimpleNews/view/adminhtml/layout/simplenews_news_grid.xml (Purpose: This file is used to declare the content of grid when you use ajax to reload the grid) and insert this following code into it:
```
<?xml version="1.0"?>
<page xmlns:xsi="http://www.w3.org/2001/XMLSchema-instance" xsi:noNamespaceSchemaLocation="../../../../../../../lib/internal/Magento/Framework/View/Layout/etc/layout_generic.xsd">
    <update handle="formkey" />
    <update handle="simplenews_news_grid_block" />
    <container name="root">
        <block class="Magento\Backend\Block\Widget\Grid\Container" name="bdc_simplenews_news.grid.container" template="Magento_Backend::widget/grid/container/empty.phtml"/>
    </container>
</page>

```


### <a name="Step2B12"> Step 2B.12:  Create news status option file</a>

- Create file: app/code/BDC/SimpleNews/Model/System/Config/Status.php (Purpose: This file is used to get News status options) and insert this following code into it:
```
<?php

namespace BDC\SimpleNews\Model\System\Config;

use Magento\Framework\Option\ArrayInterface;

class Status implements ArrayInterface {
    const ENABLED  = 1;
    const DISABLED = 0;
    /**
     * @return array
     */
    public function toOptionArray(){
        $options = [
            self::ENABLED => __('Enabled'),
            self::DISABLED => __('Disabled')
        ];

        return $options;
    }
}


```

### <a name="Step2B13"> Step 2B.13:  Create News Block for backend</a>
- Create file: app/code/BDC/SimpleNews/Block/Adminhtml/News.php (Purpose: This is the block file of grid container) and insert this following code into it:

```
<?php

namespace BDC\SimpleNews\Model\System\Config;

use Magento\Framework\Option\ArrayInterface;

class Status implements ArrayInterface {
    const ENABLED  = 1;
    const DISABLED = 0;
    /**
     * @return array
     */
    public function toOptionArray(){
        $options = [
            self::ENABLED => __('Enabled'),
            self::DISABLED => __('Disabled')
        ];

        return $options;
    }
}

```



### <a name="Step2B14">Step 2B.14:  Create Grid block file for Ajax load</a>
- Create file: app/code/BDC/SimpleNews/Block/Adminhtml/News/Grid.php (Purpose: This is the block file of grid) and insert this following code into it:
```
<?php

namespace BDC\SimpleNews\Model\System\Config;

use Magento\Framework\Option\ArrayInterface;

class Status implements ArrayInterface {
    const ENABLED  = 1;
    const DISABLED = 0;
    /**
     * @return array
     */
    public function toOptionArray(){
        $options = [
            self::ENABLED => __('Enabled'),
            self::DISABLED => __('Disabled')
        ];

        return $options;
    }
}

```

### <a name="Step2B15">Step 2B.15:  Create a backend controller file for child action class to extend</a>

- Create file: app/code/BDC/SimpleNews/Controller/Adminhtml/News.php (Purpose: I use this file as a root controller and the action classes will be extended this controller) and insert this following code into it:

```
<?php

namespace BDC\SimpleNews\Block\Adminhtml;

use Magento\Backend\Block\Widget\Grid\Container;

class News extends Container{
   /**
     * Constructor
     *
     * @return void
     */
   protected function _construct(){
        $this->_controller = 'adminhtml_news';
        $this->_blockGroup = 'BDC_SimpleNews';
        $this->_headerText = __('Manage News');
        $this->_addButtonLabel = __('Add News');
        parent::_construct();
    }
}

```


### <a name="Step2B1">Step 2B.16:  Create Backend Action file Index.php</a>

- Create file: app/code/BDC/SimpleNews/Controller/Adminhtml/News/Index.php (Purpose: This is the index action) and insert this following code into it:

```
<?php

namespace BDC\SimpleNews\Block\Adminhtml;

use Magento\Backend\Block\Widget\Grid\Container;

class News extends Container{
   /**
     * Constructor
     *
     * @return void
     */
   protected function _construct(){
        $this->_controller = 'adminhtml_news';
        $this->_blockGroup = 'BDC_SimpleNews';
        $this->_headerText = __('Manage News');
        $this->_addButtonLabel = __('Add News');
        parent::_construct();
    }
}

```


### <a name="Step2B17">Step 2B.17:  Create another Action for ajax</a>
- Create file: app/code/BDC/SimpleNews/Controller/Adminhtml/News/Grid.php (Purpose: This is the grid action which is used for loading grid by ajax) and insert this following code into it:
```
<?php

namespace BDC\SimpleNews\Controller\Adminhtml\News;

use BDC\SimpleNews\Controller\Adminhtml\News;

class Grid extends News
{
   /**
     * @return void
     */
   public function execute()
   {
      return $this->_resultPageFactory->create();
   }
}

```

![allNews](https://github.com/bdcrops/BDC_SimpleNews/blob/master/doc/allNews.png)


### <a name="Step2B8"> Step 2B.18:  Create layout file simplenews_news_edit.xml for edit form</a>
- Create file: app/code/BDC/SimpleNews/view/adminhtml/layout/simplenews_news_edit.xml (Purpose: This file is used to declare blocks which used on editing page) and insert this following code into it:
```
<?xml version="1.0"?>

<page xmlns:xsi="http://www.w3.org/2001/XMLSchema-instance"
layout="admin-2columns-left" xsi:noNamespaceSchemaLocation="../../../../../../../lib/internal/Magento/Framework/View/Layout/etc/page_configuration.xsd">
    <body>
        <referenceContainer name="left">
            <block class="BDC\SimpleNews\Block\Adminhtml\News\Edit\Tabs"
                name="bdc_simplenews_news.edit.tabs"/>
        </referenceContainer>
        <referenceContainer name="content">
            <block class="BDC\SimpleNews\Block\Adminhtml\News\Edit"
                name="bdc_simplenews_news.edit"/>
        </referenceContainer>
    </body>
</page>

```


### <a name="Step2B19">Step 2B.19:  Create the layout for create form</a>

- Create file: app/code/BDC/SimpleNews/view/adminhtml/layout/simplenews_news_create.xml and insert this following code into it:
```
<?xml version="1.0"?>

<layout xmlns:xsi="http://www.w3.org/2001/XMLSchema-instance"
xsi:noNamespaceSchemaLocation="../../../../../Magento/Core/etc/layout_single.xsd">
    <update handle="simplenews_news_edit"/>
</layout>

```


### <a name="Step2B20"> Step 2B.20:  Create a form container block</a>

- Create file: app/code/BDC/SimpleNews/Block/Adminhtml/News/Edit.php (Purpose: This is the block file of form container) and insert this following code into it:
```
<?php

namespace BDC\SimpleNews\Block\Adminhtml\News;

use Magento\Backend\Block\Widget\Form\Container;
use Magento\Backend\Block\Widget\Context;
use Magento\Framework\Registry;

class Edit extends Container
{
   /**
     * Core registry
     *
     * @var \Magento\Framework\Registry
     */
    protected $_coreRegistry = null;

    /**
     * @param Context $context
     * @param Registry $registry
     * @param array $data
     */
    public function __construct(
        Context $context,
        Registry $registry,
        array $data = []
    ) {
        $this->_coreRegistry = $registry;
        parent::__construct($context, $data);
    }

    /**
     * Class constructor
     *
     * @return void
     */
    protected function _construct()
    {
        $this->_objectId = 'id';
        $this->_controller = 'adminhtml_news';
        $this->_blockGroup = 'BDC_SimpleNews';

        parent::_construct();

        $this->buttonList->update('save', 'label', __('Save'));
        $this->buttonList->add(
            'saveandcontinue',
            [
                'label' => __('Save and Continue Edit'),
                'class' => 'save',
                'data_attribute' => [
                    'mage-init' => [
                        'button' => [
                            'event' => 'saveAndContinueEdit',
                            'target' => '#edit_form'
                        ]
                    ]
                ]
            ],
            -100
        );
        $this->buttonList->update('delete', 'label', __('Delete'));
    }

    /**
     * Retrieve text for header element depending on loaded news
     *
     * @return string
     */
    public function getHeaderText()
    {
        $newsRegistry = $this->_coreRegistry->registry('simplenews_news');
        if ($newsRegistry->getId()) {
            $newsTitle = $this->escapeHtml($newsRegistry->getTitle());
            return __("Edit News '%1'", $newsTitle);
        } else {
            return __('Add News');
        }
    }

    /**
     * Prepare layout
     *
     * @return \Magento\Framework\View\Element\AbstractBlock
     */
    protected function _prepareLayout()
    {
        $this->_formScripts[] = "
            function toggleEditor() {
                if (tinyMCE.getInstanceById('post_content') == null) {
                    tinyMCE.execCommand('mceAddControl', false, 'post_content');
                } else {
                    tinyMCE.execCommand('mceRemoveControl', false, 'post_content');
                }
            };
        ";

        return parent::_prepareLayout();
    }
}

```


### <a name="Step2B21"> Step 2B.21:  create a block for the left-side tabs</a>

- Create file: app/code/BDC/SimpleNews/Block/Adminhtml/News/Edit/Tabs.php (Purpose: This file will declare tabs at left column of the editing page) and insert this following code into it:
```
<?php

namespace BDC\SimpleNews\Block\Adminhtml\News;

use Magento\Backend\Block\Widget\Form\Container;
use Magento\Backend\Block\Widget\Context;
use Magento\Framework\Registry;

class Edit extends Container
{
   /**
     * Core registry
     *
     * @var \Magento\Framework\Registry
     */
    protected $_coreRegistry = null;

    /**
     * @param Context $context
     * @param Registry $registry
     * @param array $data
     */
    public function __construct(
        Context $context,
        Registry $registry,
        array $data = []
    ) {
        $this->_coreRegistry = $registry;
        parent::__construct($context, $data);
    }

    /**
     * Class constructor
     *
     * @return void
     */
    protected function _construct()
    {
        $this->_objectId = 'id';
        $this->_controller = 'adminhtml_news';
        $this->_blockGroup = 'BDC_SimpleNews';

        parent::_construct();

        $this->buttonList->update('save', 'label', __('Save'));
        $this->buttonList->add(
            'saveandcontinue',
            [
                'label' => __('Save and Continue Edit'),
                'class' => 'save',
                'data_attribute' => [
                    'mage-init' => [
                        'button' => [
                            'event' => 'saveAndContinueEdit',
                            'target' => '#edit_form'
                        ]
                    ]
                ]
            ],
            -100
        );
        $this->buttonList->update('delete', 'label', __('Delete'));
    }

    /**
     * Retrieve text for header element depending on loaded news
     *
     * @return string
     */
    public function getHeaderText()
    {
        $newsRegistry = $this->_coreRegistry->registry('simplenews_news');
        if ($newsRegistry->getId()) {
            $newsTitle = $this->escapeHtml($newsRegistry->getTitle());
            return __("Edit News '%1'", $newsTitle);
        } else {
            return __('Add News');
        }
    }

    /**
     * Prepare layout
     *
     * @return \Magento\Framework\View\Element\AbstractBlock
     */
    protected function _prepareLayout()
    {
        $this->_formScripts[] = "
            function toggleEditor() {
                if (tinyMCE.getInstanceById('post_content') == null) {
                    tinyMCE.execCommand('mceAddControl', false, 'post_content');
                } else {
                    tinyMCE.execCommand('mceRemoveControl', false, 'post_content');
                }
            };
        ";

        return parent::_prepareLayout();
    }
}

```

### <a name="Step2B22">Step 2B.22:  Create a block for Form information</a>

- Create file: app/code/BDC/SimpleNews/Block/Adminhtml/News/Edit/Form.php (Purpose: This file will declare form information) and insert this following code into it:
```
<?php

namespace BDC\SimpleNews\Block\Adminhtml\News;

use Magento\Backend\Block\Widget\Form\Container;
use Magento\Backend\Block\Widget\Context;
use Magento\Framework\Registry;

class Edit extends Container
{
   /**
     * Core registry
     *
     * @var \Magento\Framework\Registry
     */
    protected $_coreRegistry = null;

    /**
     * @param Context $context
     * @param Registry $registry
     * @param array $data
     */
    public function __construct(
        Context $context,
        Registry $registry,
        array $data = []
    ) {
        $this->_coreRegistry = $registry;
        parent::__construct($context, $data);
    }

    /**
     * Class constructor
     *
     * @return void
     */
    protected function _construct()
    {
        $this->_objectId = 'id';
        $this->_controller = 'adminhtml_news';
        $this->_blockGroup = 'BDC_SimpleNews';

        parent::_construct();

        $this->buttonList->update('save', 'label', __('Save'));
        $this->buttonList->add(
            'saveandcontinue',
            [
                'label' => __('Save and Continue Edit'),
                'class' => 'save',
                'data_attribute' => [
                    'mage-init' => [
                        'button' => [
                            'event' => 'saveAndContinueEdit',
                            'target' => '#edit_form'
                        ]
                    ]
                ]
            ],
            -100
        );
        $this->buttonList->update('delete', 'label', __('Delete'));
    }

    /**
     * Retrieve text for header element depending on loaded news
     *
     * @return string
     */
    public function getHeaderText()
    {
        $newsRegistry = $this->_coreRegistry->registry('simplenews_news');
        if ($newsRegistry->getId()) {
            $newsTitle = $this->escapeHtml($newsRegistry->getTitle());
            return __("Edit News '%1'", $newsTitle);
        } else {
            return __('Add News');
        }
    }

    /**
     * Prepare layout
     *
     * @return \Magento\Framework\View\Element\AbstractBlock
     */
    protected function _prepareLayout()
    {
        $this->_formScripts[] = "
            function toggleEditor() {
                if (tinyMCE.getInstanceById('post_content') == null) {
                    tinyMCE.execCommand('mceAddControl', false, 'post_content');
                } else {
                    tinyMCE.execCommand('mceRemoveControl', false, 'post_content');
                }
            };
        ";

        return parent::_prepareLayout();
    }
}

```

### <a name="Step2B23">Step 2B.23:  Create a block to declare the fields for the edit form</a>
- Create file: app/code/BDC/SimpleNews/Block/Adminhtml/News/Edit/Tab/Info.php (Purpose: This file will declare fields in form) and insert this following code into it:

```
<?php

namespace BDC\SimpleNews\Block\Adminhtml\News;

use Magento\Backend\Block\Widget\Form\Container;
use Magento\Backend\Block\Widget\Context;
use Magento\Framework\Registry;

class Edit extends Container
{
   /**
     * Core registry
     *
     * @var \Magento\Framework\Registry
     */
    protected $_coreRegistry = null;

    /**
     * @param Context $context
     * @param Registry $registry
     * @param array $data
     */
    public function __construct(
        Context $context,
        Registry $registry,
        array $data = []
    ) {
        $this->_coreRegistry = $registry;
        parent::__construct($context, $data);
    }

    /**
     * Class constructor
     *
     * @return void
     */
    protected function _construct()
    {
        $this->_objectId = 'id';
        $this->_controller = 'adminhtml_news';
        $this->_blockGroup = 'BDC_SimpleNews';

        parent::_construct();

        $this->buttonList->update('save', 'label', __('Save'));
        $this->buttonList->add(
            'saveandcontinue',
            [
                'label' => __('Save and Continue Edit'),
                'class' => 'save',
                'data_attribute' => [
                    'mage-init' => [
                        'button' => [
                            'event' => 'saveAndContinueEdit',
                            'target' => '#edit_form'
                        ]
                    ]
                ]
            ],
            -100
        );
        $this->buttonList->update('delete', 'label', __('Delete'));
    }

    /**
     * Retrieve text for header element depending on loaded news
     *
     * @return string
     */
    public function getHeaderText()
    {
        $newsRegistry = $this->_coreRegistry->registry('simplenews_news');
        if ($newsRegistry->getId()) {
            $newsTitle = $this->escapeHtml($newsRegistry->getTitle());
            return __("Edit News '%1'", $newsTitle);
        } else {
            return __('Add News');
        }
    }

    /**
     * Prepare layout
     *
     * @return \Magento\Framework\View\Element\AbstractBlock
     */
    protected function _prepareLayout()
    {
        $this->_formScripts[] = "
            function toggleEditor() {
                if (tinyMCE.getInstanceById('post_content') == null) {
                    tinyMCE.execCommand('mceAddControl', false, 'post_content');
                } else {
                    tinyMCE.execCommand('mceRemoveControl', false, 'post_content');
                }
            };
        ";

        return parent::_prepareLayout();
    }
}

```


### <a name="Step2B24">Step 2B.24:  Create a controller action for create a new News</a>
- Create file: app/code/BDC/SimpleNews/Controller/Adminhtml/News/NewAction.php (Purpose: This is the new action) and insert this following code into it:
```
<?php

namespace BDC\SimpleNews\Controller\Adminhtml\News;

use BDC\SimpleNews\Controller\Adminhtml\News;

class NewAction extends News
{
   /**
     * Create new news action
     *
     * @return void
     */
   public function execute()
   {
      $this->_forward('edit');
   }
}

```

### <a name="Step2B25">Step 2B.25:  Create Edit Action for the Edit form</a>
  - Create file: app/code/BDC/SimpleNews/Controller/Adminhtml/News/Edit.php (Purpose: This is the edit action for editing news page) and insert this following code into it:

  ```
  <?php

  namespace BDC\SimpleNews\Controller\Adminhtml\News;

  use BDC\SimpleNews\Controller\Adminhtml\News;

  class Edit extends News
  {
     /**
       * @return void
       */
     public function execute()
     {
        $newsId = $this->getRequest()->getParam('id');
          /** @var \BDC\SimpleNews\Model\News $model */
          $model = $this->_newsFactory->create();

          if ($newsId) {
              $model->load($newsId);
              if (!$model->getId()) {
                  $this->messageManager->addError(__('This news no longer exists.'));
                  $this->_redirect('*/*/');
                  return;
              }
          }

          // Restore previously entered form data from session
          $data = $this->_session->getNewsData(true);
          if (!empty($data)) {
              $model->setData($data);
          }
          $this->_coreRegistry->register('simplenews_news', $model);

          /** @var \Magento\Backend\Model\View\Result\Page $resultPage */
          $resultPage = $this->_resultPageFactory->create();
          $resultPage->setActiveMenu('BDC_SimpleNews::main_menu');
          $resultPage->getConfig()->getTitle()->prepend(__('Simple News'));

          return $resultPage;
     }
  }

  ```


### <a name="Step2B26">Step 2B.26:  A Save Action for the edit form</a>

- Create file: app/code/BDC/SimpleNews/Controller/Adminhtml/News/Save.php (Purpose: This is the save action) and insert this following code into it:
```
<?php

namespace BDC\SimpleNews\Controller\Adminhtml\News;

use BDC\SimpleNews\Controller\Adminhtml\News;

class Edit extends News
{
   /**
     * @return void
     */
   public function execute()
   {
      $newsId = $this->getRequest()->getParam('id');
        /** @var \BDC\SimpleNews\Model\News $model */
        $model = $this->_newsFactory->create();

        if ($newsId) {
            $model->load($newsId);
            if (!$model->getId()) {
                $this->messageManager->addError(__('This news no longer exists.'));
                $this->_redirect('*/*/');
                return;
            }
        }

        // Restore previously entered form data from session
        $data = $this->_session->getNewsData(true);
        if (!empty($data)) {
            $model->setData($data);
        }
        $this->_coreRegistry->register('simplenews_news', $model);

        /** @var \Magento\Backend\Model\View\Result\Page $resultPage */
        $resultPage = $this->_resultPageFactory->create();
        $resultPage->setActiveMenu('BDC_SimpleNews::main_menu');
        $resultPage->getConfig()->getTitle()->prepend(__('Simple News'));

        return $resultPage;
   }
}

```

### <a name="Step2B27">Step 2B.27:  Delete Action for the edit Form</a>

- Create file: app/code/BDC/SimpleNews/Controller/Adminhtml/News/Delete.php (Purpose: This is the delete action) and insert this following code into it:

```
<?php

namespace BDC\SimpleNews\Controller\Adminhtml\News;

use BDC\SimpleNews\Controller\Adminhtml\News;

class Delete extends News
{
   /**
    * @return void
    */
   public function execute()
   {
      $newsId = (int) $this->getRequest()->getParam('id');

      if ($newsId) {
         /** @var $newsModel \Mageworld\SimpleNews\Model\News */
         $newsModel = $this->_newsFactory->create();
         $newsModel->load($newsId);

         // Check this news exists or not
         if (!$newsModel->getId()) {
            $this->messageManager->addError(__('This news no longer exists.'));
         } else {
               try {
                  // Delete news
                  $newsModel->delete();
                  $this->messageManager->addSuccess(__('The news has been deleted.'));

                  // Redirect to grid page
                  $this->_redirect('*/*/');
                  return;
               } catch (\Exception $e) {
                   $this->messageManager->addError($e->getMessage());
                   $this->_redirect('*/*/edit', ['id' => $newsModel->getId()]);
               }
            }
      }
   }
}

```

### <a name="Step2B28"> Step 2B.28:  The mass delete action the grid list</a>

- Create file: app/code/BDC/SimpleNews/Controller/Adminhtml/News/MassDelete.php (Purpose: This file is used for deleting multi items on grid) and insert this following code into it:
```
<?php

namespace BDC\SimpleNews\Controller\Adminhtml\News;

use BDC\SimpleNews\Controller\Adminhtml\News;

class MassDelete extends News
{
   /**
    * @return void
    */
   public function execute()
   {
      // Get IDs of the selected news
      $newsIds = $this->getRequest()->getParam('news');

        foreach ($newsIds as $newsId) {
            try {
               /** @var $newsModel \Mageworld\SimpleNews\Model\News */
                $newsModel = $this->_newsFactory->create();
                $newsModel->load($newsId)->delete();
            } catch (\Exception $e) {
                $this->messageManager->addError($e->getMessage());
            }
        }

        if (count($newsIds)) {
            $this->messageManager->addSuccess(
                __('A total of %1 record(s) were deleted.', count($newsIds))
            );
        }

        $this->_redirect('*/*/index');
   }
}

```

![EditNews](https://github.com/bdcrops/BDC_SimpleNews/blob/master/doc/EditNews.png)


### <a name="Step2B29">Step 2B.29:  Backend Menu and Grid List</a>

![allNews](https://github.com/bdcrops/BDC_SimpleNews/blob/master/doc/allNews.png)

![addNews](https://github.com/bdcrops/BDC_SimpleNews/blob/master/doc/addNews.png)







## <a name="PartC"> Part C : News Module for  Front End </a>  [Go to Top](#top)

***

### <a name="Step2C1">Step 2C.1:  Create Layout file for page handle</a>

- Create file: app/code/BDC/SimpleNews/view/frontend/layout/news_news.xml (we will use this layout file as default in our module) and insert this following code into it:
```
<?xml version="1.0" encoding="UTF-8"?>

<page xmlns:xsi="http://www.w3.org/2001/XMLSchema-instance" layout="3columns"
xsi:noNamespaceSchemaLocation="../../../../../../../lib/internal/Magento/Framework/View/Layout/etc/page_configuration.xsd">
   <head>
      <css src="BDC_SimpleNews::css/style.css" />
   </head>
    <body>
       <referenceContainer name="sidebar.main">
         <block class="BDC\SimpleNews\Block\Lastest\Left" name="lestest.news.left"
             before="-" />
       </referenceContainer>

       <referenceContainer name="sidebar.additional">
         <block class="BDC\SimpleNews\Block\Lastest\Right" name="lestest.news.right"
             before="-" />
       </referenceContainer>
    </body>
</page>

```

### <a name="Step2C2">Step 2C.2:  Create another layout file by update the previous layout</a>
- Create file: app/code/BDC/SimpleNews/view/frontend/layout/news_index_index.xml (this file will declare blocks for using in the news list page) and insert this following code into it:
```
<?xml version="1.0"?>
<page xmlns:xsi="http://www.w3.org/2001/XMLSchema-instance" layout="3columns" xsi:noNamespaceSchemaLocation="urn:magento:framework:View/Layout/etc/page_configuration.xsd">
    <update handle="news_news" />
    <body>
        <referenceBlock name="content">
            <block template="BDC_SimpleNews::list.phtml" class="BDC\SimpleNews\Block\NewsList" name="jeff_simplenews_block_news_list"/>
        </referenceBlock>
    </body>
</page>

```


### <a name="Step2C3">Step 2C.3:  Create Block News List file</a>

- Create file: app/code/BDC/SimpleNews/Block/NewsList.php (this file will set the news data collection and declare pagination for them) and insert this following code into it:
```
<?php

namespace BDC\SimpleNews\Block;

use Magento\Framework\View\Element\Template;
use BDC\SimpleNews\Model\NewsFactory;

class NewsList extends Template
{
   /**
    * @var \BDC\SimpleNews\Model\NewsFactory
    */
   protected $_newsFactory;

   /**
    * @param Template\Context $context
    * @param NewsFactory $newsFactory
    * @param array $data
    */
   public function __construct(
      Template\Context $context,
      NewsFactory $newsFactory,
      array $data = []
   ) {
        $this->_newsFactory = $newsFactory;
        parent::__construct($context, $data);
   }

   /**
     * Set news collection
     */
    protected  function _construct()
    {
        parent::_construct();
        $collection = $this->_newsFactory->create()->getCollection()
            ->setOrder('id', 'DESC');
        $this->setCollection($collection);
    }

   /**
     * @return $this
     */
    protected function _prepareLayout()
    {
        parent::_prepareLayout();
        /** @var \Magento\Theme\Block\Html\Pager */
        $pager = $this->getLayout()->createBlock(
           'Magento\Theme\Block\Html\Pager','simplenews.news.list.pager'
        );
        $pager->setLimit(5)
            ->setShowAmounts(false)
            ->setCollection($this->getCollection());
        $this->setChild('pager', $pager);
        $this->getCollection()->load();

        return $this;
    }

   /**
     * @return string
     */
    public function getPagerHtml()
    {
        return $this->getChildHtml('pager');
    }
}

```

### <a name="Step2C4">Step 2C.4:  Create frontend template file list.phtml</a>

- Create file: app/code/BDC/SimpleNews/view/frontend/templates/list.phtml (this file will set the news data collection and declare pagination for them) and insert this following code into it:
```
<div class="simplenews">
   <?php
      $newsCollection = $block->getCollection();
      if ($newsCollection->getSize() > 0) :
   ?>
      <div class="toolbar top">
         <?php echo $block->getPagerHtml(); ?>
      </div>

      <ul>
         <?php foreach ($newsCollection as $news) : ?>
            <li>
               <div class="simplenews-list">
                  <a class="news-title" href="<?php echo $this->getUrl('news/index/view',
 ['id' => $news->getId()]) ?>"><?php echo $news->getTitle() ?></a>
                  <div class="simplenews-list-content">
                     <?php echo $news->getSummary() ?>
                  </div>
               </div>
            </li>
         <?php endforeach; ?>
      </ul>

      <div style="clear: both"></div>

      <div class="toolbar-bottom">
         <div class="toolbar bottom">
            <?php echo $block->getPagerHtml(); ?>
         </div>
      </div>
   <?php else : ?>
      <p><?php echo __('Have no article!') ?></p>
   <?php endif; ?>
</div>

```


### <a name="Step2C5">Step 2C.5:  Create an abstract class by extending Magento Core Action class</a>

- Create file: app/code/BDC/SimpleNews/Controller/News.php and insert this following code into it:
```
<div class="simplenews">
   <?php
      $newsCollection = $block->getCollection();
      if ($newsCollection->getSize() > 0) :
   ?>
      <div class="toolbar top">
         <?php echo $block->getPagerHtml(); ?>
      </div>

      <ul>
         <?php foreach ($newsCollection as $news) : ?>
            <li>
               <div class="simplenews-list">
                  <a class="news-title" href="<?php echo $this->getUrl('news/index/view',
 ['id' => $news->getId()]) ?>"><?php echo $news->getTitle() ?></a>
                  <div class="simplenews-list-content">
                     <?php echo $news->getSummary() ?>
                  </div>
               </div>
            </li>
         <?php endforeach; ?>
      </ul>

      <div style="clear: both"></div>

      <div class="toolbar-bottom">
         <div class="toolbar bottom">
            <?php echo $block->getPagerHtml(); ?>
         </div>
      </div>
   <?php else : ?>
      <p><?php echo __('Have no article!') ?></p>
   <?php endif; ?>
</div>

```


### <a name="Step2C6">Step 2C.6:  Update Index Controller by extends the abstract class 'New.php'</a>

- update/Edit file: app/code/BDC/SimpleNews/Controller/Index/Index.php and insert this following code into it:

```
<?php

namespace BDC\SimpleNews\Controller\Index;

use BDC\SimpleNews\Controller\News;

class Index extends News
{

    public function execute()
    {
        $pageFactory = $this->_pageFactory->create();

        $pageFactory->getConfig()->getTitle()->set($this->_dataHelper->getHeadTitle());

        //Add breadcrumb
        $breadcrumbs = $pageFactory->getLayout()->getBlock('breadcrumbs');
        $breadcrumbs->addCrumb('home', ['label'=>__('Home'), 'title'=>__('Home'), 'link'=>$this->_url->getUrl('')]);
        $breadcrumbs->addCrumb('simplenews', ['label'=>__('Simple News'), 'title'=>__('Simple News')]);

        return $pageFactory;
    }
}
```


### <a name="Step2C7"> Step 2C.7:  Create a layout file for news detail page</a>
- Create file: app/code/BDC/SimpleNews/view/frontend/web/css/style.css and insert this following code into it:
```
.simplenews > ul {
   list-style: none;
   padding: 0;
}
.simplenews > ul li {
   padding: 10px 5px;
   margin: 0;
   background-color: #fff;
   border-bottom: 1px #c4c1bc solid;
   display: inline-block;
   width: 100%;
}
.simplenews > ul li:last-child {
   border-bottom: none;
}
.simplenews-list {
   float: left;
   position: relative;
   margin-left: 10px;
   width: 100%;
}
.simplenews-list a.news-title {
   font-weight: bold;
}
.simplenews-list a.news-title:hover {
   text-decoration: none;
}
.block-simplenews .block-title {
   margin: 0px 0px 20px;
}
.block-simplenews-heading {
   font-size: 18px;
   font-weight: 300;
}

```

![frontEndNews](https://github.com/bdcrops/BDC_SimpleNews/blob/master/doc/frontEndNews.png)


### <a name="Step2C8"> Step 2C.8:  Create News view action</a>

- Create file: app/code/BDC/SimpleNews/view/frontend/layout/news_index_view.xml and insert this following code into it:
```
<?xml version="1.0" encoding="UTF-8"?>

<page xmlns:xsi="http://www.w3.org/2001/XMLSchema-instance" layout="3columns"
xsi:noNamespaceSchemaLocation="../../../../../../../lib/internal/Magento/Framework/View/Layout/etc/page_configuration.xsd">
    <update handle="news_news" />
    <body>
        <referenceContainer name="content">
            <block class="BDC\SimpleNews\Block\View" name="bdc_simplenews_news_view"
                template="BDC_SimpleNews::view.phtml" />
        </referenceContainer>
    </body>
</page>

```


### <a name="Step2C9"> Step 2C.9:  create view news block</a>

- Create file: app/code/BDC/SimpleNews/Controller/Index/View.php and insert this following code into it:

```
<?php

namespace BDC\SimpleNews\Controller\Index;

use BDC\SimpleNews\Controller\News;

class View extends News
{
    public function execute()
    {
	// Get news ID
        $newsId = $this->getRequest()->getParam('id');
	// Get news data
        $news = $this->_newsFactory->create()->load($newsId);
	// Save news data into the registry
        $this->_objectManager->get('Magento\Framework\Registry')
            ->register('newsData', $news);

        $pageFactory = $this->_pageFactory->create();

        // Add title
        $pageFactory->getConfig()->getTitle()->set($news->getTitle());

        // Add breadcrumb
        /** @var \Magento\Theme\Block\Html\Breadcrumbs */
        $breadcrumbs = $pageFactory->getLayout()->getBlock('breadcrumbs');
        $breadcrumbs->addCrumb('home',
            [
                'label' => __('Home'),
                'title' => __('Home'),
                'link' => $this->_url->getUrl('')
            ]
        );
        $breadcrumbs->addCrumb('simplenews',
            [
                'label' => __('Simple News'),
                'title' => __('Simple News'),
                'link' => $this->_url->getUrl('news')
            ]
        );
        $breadcrumbs->addCrumb('news',
            [
                'label' => $news->getTitle(),
                'title' => $news->getTitle()
            ]
        );

        return $pageFactory;
    }
}

```


### <a name="Step2C10"> Step 2C.10:  Create news view template file</a>

- Create file: app/code/BDC/SimpleNews/Block/View.php (this file will get the news data) and insert this following code into it:
```
<?php

namespace BDC\SimpleNews\Controller\Index;

use BDC\SimpleNews\Controller\News;

class View extends News
{
    public function execute()
    {
	// Get news ID
        $newsId = $this->getRequest()->getParam('id');
	// Get news data
        $news = $this->_newsFactory->create()->load($newsId);
	// Save news data into the registry
        $this->_objectManager->get('Magento\Framework\Registry')
            ->register('newsData', $news);

        $pageFactory = $this->_pageFactory->create();

        // Add title
        $pageFactory->getConfig()->getTitle()->set($news->getTitle());

        // Add breadcrumb
        /** @var \Magento\Theme\Block\Html\Breadcrumbs */
        $breadcrumbs = $pageFactory->getLayout()->getBlock('breadcrumbs');
        $breadcrumbs->addCrumb('home',
            [
                'label' => __('Home'),
                'title' => __('Home'),
                'link' => $this->_url->getUrl('')
            ]
        );
        $breadcrumbs->addCrumb('simplenews',
            [
                'label' => __('Simple News'),
                'title' => __('Simple News'),
                'link' => $this->_url->getUrl('news')
            ]
        );
        $breadcrumbs->addCrumb('news',
            [
                'label' => $news->getTitle(),
                'title' => $news->getTitle()
            ]
        );

        return $pageFactory;
    }
}

```


### <a name="Step2C11">Step 2C.11:  Create View file for News details the frontend Page</a>

- Create file: app/code/BDC/SimpleNews/view/frontend/templates/view.phtml (this file will set the news data collection and declare pagination for them) and insert this following code into it
```
<?php
   $news = $block->getNewsInformation();
?>
<div class="mw-simplenews">
   <?php echo $news->getDescription() ?>
</div>

```

![FrontendNewsDetails](https://github.com/bdcrops/BDC_SimpleNews/blob/master/doc/FrontendNewsDetails.png)


### <a name="Step2C12">Step 2C.12:  Create Latest New Block</a>

- Open file: app/code/BDC/SimpleNews/view/frontend/layout/news_news.xml (we will add 2 blocks to the page body) and insert this following code into it:
```
<?xml version="1.0" encoding="UTF-8"?>

<page xmlns:xsi="http://www.w3.org/2001/XMLSchema-instance" layout="3columns"
xsi:noNamespaceSchemaLocation="../../../../../../../lib/internal/Magento/Framework/View/Layout/etc/page_configuration.xsd">
   <head>
      <css src="BDC_SimpleNews::css/style.css" />
   </head>
    <body>
       <referenceContainer name="sidebar.main">
         <block class="BDC\SimpleNews\Block\Lastest\Left" name="lestest.news.left"
             before="-" />
       </referenceContainer>

       <referenceContainer name="sidebar.additional">
         <block class="BDC\SimpleNews\Block\Lastest\Right" name="lestest.news.right"
             before="-" />
       </referenceContainer>
    </body>
</page>

```


### <a name="Step2C13"> Step 2C.13:  Create a Block for positioning the latest news: Left or Right</a>
- Create file: app/code/BDC/SimpleNews/Block/Lastest.php (this file will get the news data) and insert this following code into it:

```
<?php

namespace BDC\SimpleNews\Block;

use Magento\Framework\View\Element\Template;
use BDC\SimpleNews\Helper\Data;
use BDC\SimpleNews\Model\NewsFactory;
use BDC\SimpleNews\Model\System\Config\Status;

class Lastest extends Template
{
   /**
    * @var \BDC\SimpleNews\Helper\Data
    */
   protected $_dataHelper;

   /**
    * @var \BDC\SimpleNews\Model\NewsFactory
    */
   protected $_newsFactory;

   /**
    * @param Template\Context $context
    * @param Data $dataHelper
    * @param NewsFactory $newsFactory
    */
   public function __construct(
      Template\Context $context,
      Data $dataHelper,
      NewsFactory $newsFactory
   ) {
      $this->_dataHelper = $dataHelper;
      $this->_newsFactory = $newsFactory;
      parent::__construct($context);
   }

   /**
    * Get five latest news
    *
    * @return \BDC\SimpleNews\Model\Resource\News\Collection
    */
   public function getLatestNews()
   {
      // Get news collection
      $collection = $this->_newsFactory->create()->getCollection();
      $collection->addFieldToFilter(
         'status',
         ['eq' => Status::ENABLED]
      );
      $collection->getSelect()
         ->order('id DESC')
         ->limit(5);

      return $collection;
   }
}


```


### <a name="Step2C14"> Step 2C.14:  Create the template file for Latest News</a>

- Create file: app/code/BDC/SimpleNews/Block/Lastest/Left.php (This file will check the left position and set template file) and insert this following code into it:

```
<?php

namespace BDC\SimpleNews\Block\Lastest;

use BDC\SimpleNews\Block\Lastest;
use BDC\SimpleNews\Model\System\Config\LastestNews\Position;

class Left extends Lastest
{
   public function _construct()
   {
      $position = $this->_dataHelper->getLastestNewsBlockPosition();
      // Check this position is applied or not
      if ($position == Position::LEFT) {
         $this->setTemplate('BDC_SimpleNews::lastest.phtml');
      }
   }
}

```

- Create file: app/code/BDC/SimpleNews/Block/Lastest/Right.php (This file will check the right position and set template file) and insert this following code into it:

```
<?php

namespace BDC\SimpleNews\Block\Lastest;

use BDC\SimpleNews\Block\Lastest;
use BDC\SimpleNews\Model\System\Config\LastestNews\Position;

class Right extends Lastest
{
   public function _construct()
   {
      $position = $this->_dataHelper->getLastestNewsBlockPosition();
      // Check this position is applied or not
      if ($position == Position::RIGHT) {
         $this->setTemplate('BDC_SimpleNews::lastest.phtml');
      }
   }
}

```


### <a name="Step2C15">Step 2C.15:  Frontend view for the module</a>

- Create file: app/code/BDC/SimpleNews/view/frontend/templates/lastest.phtml (This file will display 5 lastest news on the page) and insert this following code into it:
```
<?php
   $latestNews = $block->getLatestNews();
   if ($latestNews->getSize() > 0) :
?>
   <div class="block block-simplenews">
      <div class="block-title">
         <strong class="block-simplenews-heading"><?php echo __('Latest News') ?></strong>
      </div>

      <div class="block-content">
         <?php foreach ($latestNews as $news) : ?>
            <div>
               <span>+ </span>
               <a href="<?php echo $this->getUrl('news/index/view', ['id' => $news->getId()])
?>">
                  <span><?php echo $news->getTitle() ?></span>
               </a>
            </div>
         <?php endforeach; ?>
      </div>
   </div>
<?php endif; ?>

```
[Go to Top](#top)




## Ref
***
https://devdocs.magento.com/guides/v2.3/extension-dev-guide/declarative-schema/

https://onilab.com/blog/declarative-schema-magento-2-3-and-higher/

https://www.mage-world.com/blog/create-a-module-with-custom-database-table-in-magento-2.html

http://techjeffyu.com/blog/magento-2-a-full-magento-2-module

https://github.com/codingarrow/M2/tree/master/BDC/SimpleNews
