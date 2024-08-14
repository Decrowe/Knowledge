 - Since 2016
- Extends concepts of Micro-Services
- Composition of many small features
- Features owned by seperate teams

## Background

![[monolith-frontback-microservices.png]]
## Comparison 

### Monolith
#### Pro:
- All code at one place
#### Con:
- One Team for everything
- Projects grows and gets more and more complicated and harder to maintain
- Huge code base
- Long compile times

### Front & Back
#### Pro:
- Seperation of responsibilities and focus
#### Con:
- Projects still grow and get hard to maintain
- shorter compile times

### Microservices
#### Pro:
- Services splitted up; easy to handle and maintain
- Seperation of functionality
- Frontend only uses relevant services/functionality
- Services easy to exchange
- Good Seperation of responsibilities and focus for each service
#### Con:
- Huge number of services may confuse
- Short compile times

## How to combine the individual features
- Many Approaches
- Plain linking of HTML and JS files
- [[Module Federation]]

Sources: 
- Images: https://micro-frontends.org/