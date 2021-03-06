# Builder Design Pattern – 

It lets us create a complex object on step-by-step basis  

**Problem:**  
Consider a Car class, which has a long list of attriutes.  

and assume, Not all the attributes are mandatory while instantiating the Car class.  

![image](https://user-images.githubusercontent.com/26399543/152674773-fcf2921d-a513-4edc-93c2-e4207ddf096e.png)  


There are 2 ways to approach towards creating the instance of this class.  

**Case-1:** Create a single constructor using all the attributes  
and then create instances like this -  
![image](https://user-images.githubusercontent.com/26399543/152674791-ae02de79-4654-4815-98f2-86a7642268f4.png)  

**Case-2:** Create all possible constructors from the combination of the attributes  
and then create instances like this -  
![image](https://user-images.githubusercontent.com/26399543/152674812-642af8f5-9136-40db-9283-b929ecbcb1f2.png)  

Well, there's problem in both of the above approaches,  
in first case, it doe not work well with optional attributes, we still need to supply null in the right position (which is an overhead)  
in 2nd case, we would end up having a large number of constructors (difficult to maintain)  

This is where, Builder Pattern helps us  


**Fluent Builder:**  
```java
package com.design.pattern.builder;

class Person {
	// address
	public String streetAddress, postcode, city;

	// employment
	public String companyName, position;
	public int annualIncome;

	@Override
	public String toString() {
		return "Person{" + "streetAddress='" + streetAddress + '\'' + ", postcode='" + postcode + '\'' + ", city='"
				+ city + '\'' + ", companyName='" + companyName + '\'' + ", position='" + position + '\''
				+ ", annualIncome=" + annualIncome + '}';
	}
}

// builder facade
class PersonBuilder {
	// the object we're going to build
	protected Person person = new Person(); // reference!

	public PersonJobBuilder works() {
		return new PersonJobBuilder(person);
	}

	public PersonAddressBuilder lives() {
		return new PersonAddressBuilder(person);
	}

	public Person build() {
		return person;
	}
}

class PersonAddressBuilder extends PersonBuilder {
	public PersonAddressBuilder(Person person) {
		this.person = person;
	}

	public PersonAddressBuilder at(String streetAddress) {
		person.streetAddress = streetAddress;
		return this;
	}

	public PersonAddressBuilder withPostcode(String postcode) {
		person.postcode = postcode;
		return this;
	}

	public PersonAddressBuilder in(String city) {
		person.city = city;
		return this;
	}
}

class PersonJobBuilder extends PersonBuilder {
	public PersonJobBuilder(Person person) {
		this.person = person;
	}

	public PersonJobBuilder at(String companyName) {
		person.companyName = companyName;
		return this;
	}

	public PersonJobBuilder asA(String position) {
		person.position = position;
		return this;
	}

	public PersonJobBuilder earning(int annualIncome) {
		person.annualIncome = annualIncome;
		return this;
	}
}

/**
 * Builder Facets Demo
 * 
 * @author manoranjan.kumar
 */
class Demo2 {
	public static void main(String[] args) {
		PersonBuilder pb = new PersonBuilder();
		Person person = pb.lives()
                          .at("123 London Road")
                          .in("London")
                          .withPostcode("SW12BC")
                      .works()
                          .at("Fabrikam")
                          .asA("Engineer")
                          .earning(123000)
                      .build();
		System.out.println(person);
	}
}
```





**Reference:**  
1. https://www.youtube.com/watch?v=MaY_MDdWkQw

