# GadgetHub

An online electronics store built with ASP.NET MVC 5 and Entity Framework. Customers browse products by category, add them to a cart, and check out. Admins log in to add, edit, and delete products.

It follows the store architecture from Adam Freeman's *Pro ASP.NET MVC 5* ("SportsStore"), adapted into a gadget shop.

## Features

- Paged product listing with category navigation
- Session-based shopping cart using a custom model binder
- Checkout that collects shipping details and emails the order
- Password-protected admin area with full product CRUD and image upload
- Dependency injection with Ninject, so controllers depend on interfaces (`IProductRepository`, `IOrderProcessor`) instead of concrete classes

## Structure

```
GadgetHub.sln
GadgetHub.Domain/     Entities (Product, Cart, ShippingDetails), repository and order interfaces, EF implementations
GadgetHub.WebUI/      MVC controllers, views, HTML helpers, Ninject setup, auth
SQLQueries/           Scripts to create and seed the Products table
```

## Running it

Requires Visual Studio with the ASP.NET workload and SQL Server LocalDB (.NET Framework 4.7.2).

1. Open `GadgetHub.sln`. NuGet restores the packages on build.
2. Run the scripts in `SQLQueries/` against `(localdb)\MSSQLLocalDB` to create the `GadgetHub` database and seed products.
3. Set `GadgetHub.WebUI` as the startup project and run.

The SMTP settings in `EmailOrderProcessor` are placeholders. Fill them in to actually send order emails.
