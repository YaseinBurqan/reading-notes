# Read Me File

# Sequelize-Normalization

## Associations

To do this, Sequelize provides four types of associations that should be combined to create them:

    - The HasOne association
    - The BelongsTo association
    - The HasMany association
    - The BelongsToMany association

## Defining the Sequelize associations

- The four association types are defined in a very similar way. Let's say we have two models, A and B. Telling Sequelize that you want an association between the two needs just a function call:

##

    const A = sequelize.define('A', /*...*/);
    const B = sequelize.define('B', /*...*/);

    A.hasOne(B); // A HasOne B
    A.belongsTo(B); // A BelongsTo B
    A.hasMany(B); // A HasMany B
    A.belongsToMany(B, { through: 'C' }); // A BelongsToMany B through the junction table C

- They all accept an options object as a second parameter (optional for the first three, mandatory for belongsToMany containing at least the through property):

##

    A.hasOne(B, { /*options*/ });
    A.belongsTo(B, { /*options*/ });
    A.hasMany(B, { /*options*/ });
    A.belongsToMany(B, { through: 'C', /*options*/ });

#

## Creating the standard relationships

To create a One-To-One relationship:

    the hasOne and belongsTo associations are used together.

To create a One-To-Many relationship:

     the hasMany and belongsTo associations are used together.

To create a Many-To-Many relationship:

    two belongsToMany calls are used together.

## Basics of queries involving associations

    With the basics of defining associations covered, we can look at queries involving associations. The most common queries on this matter are the read queries (i.e. SELECTs).

## Fetching associations - Eager Loading vs Lazy Loading

    The concepts of Eager Loading and Lazy Loading are fundamental to understand how fetching associations work in Sequelize. Lazy Loading refers to the technique of fetching the associated data only when you really want it; Eager Loading, on the other hand, refers to the technique of fetching everything at once, since the beginning, with a larger query.

### Lazy Loading example

    const awesomeCaptain = await Captain.findOne({
     where: {
    name: "Jack Sparrow"
    }
    });
    // Do stuff with the fetched captain
    console.log('Name:', awesomeCaptain.name);
    console.log('Skill Level:', awesomeCaptain.skillLevel);
    // Now we want information about his ship!
    const hisShip = await awesomeCaptain.getShip();
    // Do stuff with the ship
    console.log('Ship Name:', hisShip.name);
    console.log('Amount of Sails:', hisShip.amountOfSails);

### Eager Loading Example

    const awesomeCaptain = await Captain.findOne({
     where: {
    name: "Jack Sparrow"
     },
    include: Ship
    });
    // Now the ship comes with it
    console.log('Name:', awesomeCaptain.name);
    console.log('Skill Level:', awesomeCaptain.skillLevel);
    console.log('Ship Name:', awesomeCaptain.ship.name);
    console.log('Amount of Sails:', awesomeCaptain.ship.amountOfSails);
