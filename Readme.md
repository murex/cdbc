# CDBC

Database access library for C++.

## About

Why does C++ need another database access library? First, nothing has been standardized yet. Secondly, we did not found a library which satisfied our needs of abstraction:
1. Driver abstraction: the API should be the same regardless of the database vendor.
2. SQL syntax abstraction: the API user should be able to write portable SQL queries regardless of the underlying vendor.
3. Runtime driver selection: user code should be able to switch accross database vendors at runtime without any need to recompile.
4. No data model definition: user code should be able to access the database without providing the data model to the API. ORM should be built on top of `CDBC` and not the other way around.

`CDBC` tries to answer those requirements by providing a common abstraction of sql execution accross databases and at the same time an abstraction of the SQL dialect used by database. It offers a low-level building block for applications and higher level frameworks alike.

We have built upon the previous work of Johan Anhofer published as [N3886: A proposal to add a Database Access Layer to the Standard Library](http://www.open-std.org/jtc1/sc22/wg21/docs/papers/2014/n3886.pdf "N3886 draft"), amended it on some parts and completed it mainly on SQL dialect abstraction.
We plan to write and submit a draft proposal to the C++ normalization committee.


*We are currently open sourcing the library. We plan to finish this before mid October.*


## Documentation

Here a very simple bootstrap example to perform a simple select on a `SQLite` in-memory database.
```cpp
#include <iostream>
#include <string>

#include <murex/db/db_api.hpp>

using namespace murex::db;

int main(int argc, char** argv) {
    connection cnx("sqlite");
    cnx.open(":memory:");
    statement stm("select * from EMPLOYEES", cnx);

    for (result res(stm.execute()); !res.is_eof(); res.move_next() {
        std::cout
            << "- "          << res.get<std::string>("NAME")
	        << ", age:"      << res.get<int>("AGE")
	        << ", salary: $" << res.get<double>("SALARY")
	        << '\n';
    }
    return 0;
}
```

And the same example using the DSL to abstract the SQL dialect:
```cpp
#include <iostream>
#include <string>

#include <murex/db/db_api.hpp>

using namespace murex::db;

int main(int argc, char** argv) {
    connection cnx("sqlite");
    cnx.open(":memory:");
    statement stm(statement_builder(cnx)
                    .from("EMPLOYEES")
                    .select("NAME", "AGE", "SALARY")
                    .to_statement());

    for (result res(stm.execute()); !res.is_eof(); res.move_next() {
        std::cout
            << "- "          << res.get<std::string>("NAME")
	        << ", age:"      << res.get<int>("AGE")
	        << ", salary: $" << res.get<double>("SALARY")
	        << '\n';
    }
    return 0;
}
```

The DSL use natural expressions composition to build a filter:
```cpp
statement stm(statement_builder(cnx)
                .from("EMPLOYEES")
		        .where(column("AGE") > var("max_age") &&
		            column("SALARY") < var("min_salary"))
                .select("NAME")
		        .to_statement());

stm.bind(var("max_age"), 50)
   .bind(var("min_salary", 42000.0))

result res(stm.execute());
```


## Supported Compilers

The code is known to work on the following compilers:
- Visual Studio 2008
- GCC 3.4
- clang 3.8

**Development Status:** This code is still under heavy development on our side. However, it is well-tested and will be put in production soon.


## Contributing

The `master` branch of this repository contains the latest stable changes of CDBC. Pull requests should be submitted against the latest head of master. See CONTRIBUTING.md for more details about how to contribute.
