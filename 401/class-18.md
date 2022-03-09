# Reading Notes 18 -- Web App Security


## Many to Many

From [Baeldung Article](https://www.baeldung.com/hibernate-many-to-many)

An entity that can be related to many instances of another entity, and that other entity can be related to many instances of the first entity defines a "many to many" relationship. In Spring we can use the @ManyToMany annoation.

- @ManyToMany can take a cascade value.
- @JoinTable can be used to link related tables to be used in the relationship.
  - @JoinColum is used inside of the table join to identify where the join is happening.

The @ManyToMany annoation has an owner side and an inverse of the owning side. The table joins happen on the owning side. The mappedBy attribute is used on the inverse of the owning side to declare which value it is mapped with.

### This World of Ours

[Humorous Security Overview](https://scholar.harvard.edu/files/mickens/files/thisworldofours.pdf)

I'm not exactly sure what I just read but my take away is that Security is hard, everything is out to get you, and you just need to try your best to be as smart and careful as you can.
