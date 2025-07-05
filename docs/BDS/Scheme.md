## Technical Specification

BDS is formally defined by an XML Schema (XSD) version 1.0. The key components of the schema include:

### BDS (Root Element)

Defines the overall document structure:

* Attributes: `Version` (required), `Name` (optional)
* Elements:

  * `<Description>`
  * `<FileVersion>`
  * `<ScheduleSets>`: collection of `<ScheduleSet>`
  * `<ResponsibleParty>`

### ScheduleSet

Groups multiple schedules:

* Attributes: `Name`
* Optional elements: `<Description>`, `<Group>`, `<Discipline>`
* Contains: one or more `<Schedule>` elements

### Schedule

Defines one schedule template:

* Attributes: `Name`
* Contains:

  * `<Description>` (optional text)
  * `<IfcClasses>`: list of applicable IFC types
  * `<Fields>`: one or more `PropertyField` or `AttributeField`
  * `<Filters>`: optional list of filter conditions
  * `<Sort>`: optional list of sort conditions
  * `<Group>`: optional field grouping definition  

### PropertyField

Defines a schedule column from an IFC property:

```xml
<PropertyField Id="DoorWidth">
  <PropertySetName>Dimensions</PropertySetName>
  <PropertyName>Width</PropertyName>
</PropertyField>
```

### AttributeField

Defines a column from an IFC attribute:

```xml
<AttributeField Id="DoorName">
  <Attribute>ObjectName</Attribute>
</AttributeField>
```

### Filter

Defines a conditional rule:

```xml
<Filter>
  <Field>DoorWidth</Field>
  <Operator>GreaterThan</Operator>
  <Value>0.8</Value>
</Filter>
```

### Sort

Defines how to order rows:

```xml
<Sort>
  <Field>DoorName</Field>
  <Order>Ascending</Order>
</Sort>
```

### Example Structure

```xml
<BDS Name="ExampleSchedules" Version="1.0">
  <Description>Standard schedules for Project X</Description>
  <FileVersion>1.0.0</FileVersion>
  <ScheduleSets>
    <ScheduleSet Name="General">
      <Discipline>Architectural</Discipline>
      <Schedules>
        <Schedule Name="DoorSchedule">
          <IfcClasses>
            <IfcClass>IfcDoor</IfcClass>
          </IfcClasses>
          <Fields>
            <PropertyField Id="DoorWidth">
              <PropertySetName>Dimensions</PropertySetName>
              <PropertyName>Width</PropertyName>
            </PropertyField>
            <AttributeField Id="DoorName">
              <Attribute>ObjectName</Attribute>
            </AttributeField>
          </Fields>
          <Filters>
            <Condition>
              <Field>DoorWidth</Field>
              <Operator>GreaterThan</Operator>
              <Value>0.8</Value>
            </Condition>
          </Filters>
          <Sort>
            <Condition>
              <Field>DoorName</Field>
              <Order>Ascending</Order>
            </Condition>
          </Sort>
        </Schedule>
      </Schedules>
    </ScheduleSet>
  </ScheduleSets>
  <ResponsibleParty>Acme BIM Team</ResponsibleParty>
</BDS>
```

This structure enables software tools to interpret and apply standard data queries across different BIM environments, ensuring consistency, repeatability, and collaboration.
