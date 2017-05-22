# XML
> Extensible Mark-up Language
- XML is sort of metadata, designed to describe the meaning of the data
- Ability to define custom tags
### Example:

```php
<?xml version="1.0" encoding="UTF-8"?>
<studentDatabase>
    <student studentID="01">
        <firstName> John </firstName>
        <middleName> Robert </middleName>
        <lastname> Tailor </lastname>
        <course> Computer Science </course>
    </student>
    <student studentID="02">
        <firstName> Ali </firstName>
        <lastName> Mohammed </lastName>
        <course> Computing for Business </course>
    </student>
</studentDatabase>
```
## Namespaces
> A namespace is used to uniquely identify a collection of element type and attribute names


- Using a **prefix** we create two different types of <table> elements, however you must define a **namespace**

```markup
<h:table xmlns:h="http://www.w3.org/TR/html4/">
    <h:tr>
        <h:td> Name </h:td>
    </h:tr>
</h:table>

<f:table xmlns:f="htttps://www.w3schools.com/furniture">
    <f:name> Coffee Table </f:name>
    <f:width> 80 </f:width>
    <f:length> 120 </f:length>
</f:table>

<!-- Alternatively, you can define namespaces in the root -->
<root
xmlns:h="link"
xmlns:f="another-one">

    ...

</root>
```


## XML Schemas
> XML Schema describes the structure of an XML document. The schema language is also referred to as **XML Schema Definition (XSD)**
- It defines:
  - elements that can appear in a document
  - attributes that can appear in a document
  - which elements are child elements
  - the order of child elements
  - the number of child elements
  - whether an element is empty or can include text
  - data types for elements and attributes
  - default and fixed values for elements and attributes
> XML Schemas are written in XML and support data types, namespaces and even regex! Schemas are a more object oriented approach to XML, than the old DTD (Document Type Definition).


### Example:

```markup
<?xml version="1.0"?>
<xs:schema xmlns:xs="http://www.w3.org/2001/XMLSchema">
<xs:element name="note">
    <xs:complexType>
        <xs:sequence>
            <xs:element name="to" type="xs:string"/>
            <xs:element name="from" type="xs:string"/>
            <xs:element name="heading" type="xs:string"/>
            <xs:element name="body" type="xs:string"/>
        </xs:sequence>
    </xs:complexType>
</xs:element>
</xs:schema>
```
### Reference to an XML Schema
- Default namespace declaration

```markup
<xs:schema xmlns="http://www.w3schools.com">
```


### Restrictions on values
> Restrictions are used to define acceptable values for XML elements or attributes

```markup
<xs:element name="age">
    <xs:simpleType>
        <xs:restriction base="xs:integer">
            <xs:minInclusive value="0"/>
            <xs:maxInclusive value="120"/>
        </xs:restriction>
    </xs:simpleType>
</xs:element>
```
- To limit the content of an XML element to a set of acceptable values, use the enumeration constraint

```markup
<xs:element name="car">
    <xs:simpleType>
        <xs:restriction base="xs:string">
            <xs:enumeration value="Audi"/>
            <xs:enumeration value="Golf"/>
            <xs:enumeration value="BMW"/>
        </xs:restriction>
    </xs:simpleType>
</xs:element> 
```


### Restrictions for Data types
> **enumeration** - Defines a list of acceptable values
> **fractionDigits** - Specifies the maximum number of decimal places allowed. Must be equal to or greater than zero
> **length** - Specifies the exact number of characters or list items allowed. Must be equal to or greater than zero
> **maxExclusive** - Specifies the upper bounds for numeric values (the value must be less than this value)
> 
**maxInclusive** - Specifies the upper bounds for numeric values (the value must be less than or equal to this value)
> 
**maxLength** - Specifies the maximum number of characters or list items allowed. Must be equal to or greater than zero
> 
**minExclusive** - Specifies the lower bounds for numeric values (the value must be greater than this value)
> 
**minInclusive** - Specifies the lower bounds for numeric values (the value must be greater than or equal to this value)
> **minLength** - Specifies the minimum number of characters or list items allowed. Must be equal to or greater than zero
> **pattern** - Defines the exact sequence of characters that are acceptable
> **totalDigits** - Specifies the exact number of digits allowed. Must be greater than zero
> **whiteSpace** - Specifies how white space (line feeds, tabs, spaces, and carriage returns) is handled


