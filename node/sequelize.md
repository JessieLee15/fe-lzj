# sequelize


## note
* mysql2@^1.5.2
* Supports Node v6 and above to use ES6 features
* model 中get属性值：getDataValue()不会调用属性的getter，this.会调用getter
* timestamps: add the attributes createdAt and updatedAt to your model

* model init options：
  * modelName：'bar'
    * The name of the model. The model will be stored in `sequelize.models` under this name.This defaults to class name i.e. Bar in this case.
    * This will control name of auto-generated foreignKey and association naming
  * timestamps：false
    * don't add the timestamp attributes (updatedAt, createdAt)
  * paranoid: true
    * don't delete database entries but set the newly added attribute deletedAt to the current date (when deletion was done)
    * paranoid will only work if timestamps are enabled
  * underscored: true
    * Will automatically set field option for all attributes to snake cased name
    * Does not override attribute with field option already defined
  * freezeTableName: true
    * disable the modification of table names
    * By default, sequelize will automatically transform all passed model names (first parameter of define) into plural
    * if you don't want that, set true
  * tableName: 'my_very_custom_table_name'
    * define the table's name
  * version: true
    * Enable optimistic locking
    * When enabled, sequelize will add a version count attribute to the model and throw an OptimisticLockingError error when stale instances are saved
  * sequelize
    * Sequelize instance
  * comment: "I'm a table comment!"

  ### query
  * ```as```If an association is aliased (using the as option), you must specify this alias when including the model. Notice how the user's Tools are aliased as Instruments above. In order to get that right you have to specify the model you want to load, as well as the alias
  * By default, associations are loaded using a left join

## TODO 
* transaction：前提：node线程
* 创建model方式：extend model，sequelize.define
* sequelize-auto： 数据库表 => model
* Migrations: 迁移数据库 on  production
* 'protecting' properties that map to database fields and for defining 'pseudo' properties[Getters & setters]
* sequelize.sync中的match
* Indexes
* 复习left join、right join、inner join
* sequelize hooks
* 

> As shown above by the extensive usage of .then calls, Sequelize uses Promises extensively. This means that, if your Node version supports it, you can use ES2017 async/await syntax for all asynchronous calls made with Sequelize.
> Also, all Sequelize promises are in fact Bluebird promises, so you have the rich Bluebird API to use as well (for example, using finally, tap, tapCatch, map, mapSeries, etc). You can access the Bluebird constructor used internally by Sequelize with Sequelize.Promise, if you want to set any Bluebird specific options.




