## Ex-27 Create a Hospital patient data management application using react,SpringBoot and SQL
## Aim:
To create a Hospital application using SpringBoot and SQL.

## Algorithm:
### Step 1:-
Open Spring Initialzr.

### Step 2:-
Save the zip file.

### Step 3:-
Open an IDE like IntelliJ,Oracle etc.

### Step 4:-
Open the folder in the IDE.

### Step 5:-
Create Components.

### Step 6:-
Connect the database with the SpringBoot.

## Program:
Hospital.java
```java
package com.hospital.hosman.hos;

import jakarta.persistence.*;
import org.junit.platform.commons.annotation.Testable;
import org.springframework.boot.autoconfigure.domain.EntityScan;

import java.time.LocalDate;
import java.time.Period;

@Entity
@Table
public class Hosman {
    @Id
    @SequenceGenerator(
            name = "hosman_sequence",
            sequenceName = "hosman_sequence",
            allocationSize = 1
    )
    @GeneratedValue(
            strategy = GenerationType.SEQUENCE,
            generator = "hosman_sequence"
    )
    private Long PatId;
    private String PatName;
    @Transient
    private Integer PatAge;
    private LocalDate PatDob;
    private String PatEmail;

    public Hosman() {
    }

    public Hosman(Long patId, String patName, LocalDate patDob, String patEmail) {
        this.PatId = patId;
        this.PatName = patName;
        this.PatDob = patDob;
        this.PatEmail = patEmail;
    }

    public Long getPatId() {
        return PatId;
    }

    public void setPatId(Long patId) {
        PatId = patId;
    }

    public String getPatName() {
        return PatName;
    }

    public void setPatName(String patName) {
        PatName = patName;
    }

    public Integer getPatAge() {
        return Period.between(PatDob,LocalDate.now()).getYears();
    }

    public void setPatAge(Integer patAge) {
        PatAge = patAge;
    }

    public LocalDate getPatDob() {
        return PatDob;
    }

    public void setPatDob(LocalDate patDob) {
        PatDob = patDob;
    }

    public String getPatEmail() {
        return PatEmail;
    }

    public void setPatEmail(String patEmail) {
        PatEmail = patEmail;
    }

    @Override
    public String toString() {
        return "Hosman{" +
                "PatId=" + PatId +
                ", PatName='" + PatName + '\'' +
                ", PatAge=" + PatAge +
                ", PatDob=" + PatDob +
                ", PatEmail='" + PatEmail + '\'' +
                '}';
    }
}
```
applications.properties
```java
spring.datasource.url=jdbc:postgresql://localhost:5432/hosman_db
spring.datasource.username=postgres
spring.datasource.password=sk@2003
spring.jpa.hibernate.ddl-auto=create-drop
spring.jpa.show-sql=true
spring.jpa.properties.hibernate.dialect=org.hibernate.dialect.PostgreSQLDialect
spring.jpa.properties.hibernate.format_sql=true
```
App.js
```java
import React from "react"
import './App.css';
import { BrowserRouter as Router, Route, Routes, Link } from "react-router-dom";
import ecomComponent from './components/hosComponent/hosComponent';
import HeaderComponent from "./components/HeaderComponent/HeaderComponent";
import hosComponent from "./components/hosComponent/hosComponent";
import hosComponent from "./components/hosComponent/hosComponent";

function App() {
  return (
    <Router>
            <div className="container">
              <HeaderComponent/>
              
            <nav className="nav-menu">
                <Link to="/" >Home</Link>
                <Link to="/admin/add" >Add Member</Link>
                <Link to="/admin/delete" >Delete Member</Link>
            </nav>
           <Routes>
                 <Route exact path='/' element={<ecomComponent/>}></Route>
                 <Route path='/admin/add' element={<ecomComponent/>}></Route>
                 <Route path='/admin/delete' element={<ecomComponent/>}></Route>
          </Routes>
          </div>
       </Router>
  );
}

export default App;
```
## Output:
![hospital](https://github.com/SarankumarJ/Hospital-management/assets/94778101/7dc177b2-dac2-4c0c-931c-8e1efcf5a427)


## Result:
Thus we have successfully created a Hospital application using SpringBoot and SQL.
