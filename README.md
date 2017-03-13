# FarMar: The Farmers' Market Finder
In this assignment we will be assessing your ability to create classes, instance methods, class methods & write tests. We will use __CSV__ files as our _database_.

This project is based off the [Farmar project](https://www.github.com/adagold/farmar) in the AdaGold repository.  Fork & Clone the repository for your work on the project.  

## Learning Goals
- Reinforce and practice all of the Ruby and programming concepts we've covered in class
  - Practice writing specs and using TDD
  - Practice working with raw data and using it to create _instances_ of a Ruby class
  - Practice working with multiple files in a single project.

## Project Setup and Expectations
### Project Structure
Create a Ruby class to represent each kind of data in the `support/` directory. Your implementation will have _class methods_ to handle finding, sorting, and collecting the data into _instances_ representing individual rows of data. Each of those _instances_ will have _instance methods_ to provide details about the object.

#### Encapsulation
To manage our data classes we will use a file named `/far_mar.rb`. It should look something like:

```ruby
# gems your project needs
require 'csv'

# our namespace module
module FarMar; end

# all of our data classes that live in the module
require 'lib/farmar_market'
# ...require all needed classes
```

Each _class_ you build will live in the `/lib` directory, and belong to the `FarMar` _module_:

```ruby
# lib/farmar_market.rb
class FarMar::Market
  # Your code goes here
end
```

The module provides a _namespace_ for the application. A _namespace_ ensures the _classes_ we create will not 'collide' or 'overlap' with a _class_ that could exist elsewhere in a codebase (like in a gem).


### Specs & Testing
- Coverage
	-  You must have __90% test coverage__ from `simplecov`. The HTML files that are generated from `simplecov` should _not_ be included in your git repository. Tests should be in the form of __minitest specs__.
-  Use the `spec_helper.rb` so that all of your tests run when you run `$ rake` from the project root.
- You will write spec-style tests to test each of the methods, including initialize, of Market & Vendor
	- All test files should be in the `specs` folder
	- Test nominal & edge-cases for each method.  At least 2 test-cases for each method.  
	- Use `let` &/or `before` as appropriate to DRY up your code.

### Project Data
#### FarMar::Market
Each individual market has many vendors associated with it. The `FarMar::Market` data, in order in the CSV, consists of:

1. ID - (Integer) a unique identifier for that market
2. Name - (String) the name of the market (not guaranteed unique)
3. Address - (String) street address of the market
4. City - (String) city in which the market is located
5. County - (String) county in which the market is located
6. State - (String) state in which the market is located
7. Zip - (String) zipcode in which the market is located

#### FarMar::Vendor
Each vendor belongs to a market, the `market_id` field refers to the `FarMar::Market` ID field.
Each vendor has many products for sell. The `FarMar::Vendor` data, in order in the CSV, consists of:

1. ID - (Integer) uniquely identifies the vendor
2. Name - (String) the name of the vendor (not guaranteed unique)
3. No. of Employees - (Integer) How many employees the vendor has at the market
4. Market_id - (Integer) a reference to which market the vendor attends


## Requirements
### Baseline
#### Project Setup
1. Fork the [repo](https://github.com/CheezItMan/farmar) to your Github account.
1. Clone your fork to your projects directory, and `cd` into the cloned repo.


#### Baseline Requirements
- Create a Market & Vendor class.
- You should be able to create instances of these classes that know about their associated data file.
- Create your `far_mar.rb` file which will bring together all classes created in the previous step.
- Complete the boilerplate necessary for testing. You should be able to `$ rake` from the project root to run your specs. Have at least one spec to verify this setup before submitting your baseline.

## Primary Requirements
### For each of the data classes build the following methods:
1. `self.all`: returns a collection of instances, representing all of the objects described in the CSV
1. `self.find(id)`: returns an instance of the object where the value of the `id` field in the CSV matches the passed parameter.

### Additional FarMar::Market Methods
1. `#vendors`: returns a collection of `FarMar::Vendor` instances that are associated with the market by the `market_id` field.

### Additional FarMar::Vendor Methods
1.  `#market`: returns the market associated with this vendor.
