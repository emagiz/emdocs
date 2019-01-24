# eMagiz as an iPaaS

| point to point | many to many | 
| :------------: | :----------: | 
| <img width="210" height="70" src="point-to-point.png"> | <img width="280" height="140" src="more-many-to-many.png"> | 

In the first image you can see a stand-alone message flow represented by a **point-to-point connection** (one integration). When there are more integrations needed the effectiveness of single message flows decreases. A situation like the one in the second image which represents a **many-to-many connection** cannot be solved by only using stand-alone message flows in an effective way.  
This is where a CDM - cannonical (common) data model becomes needed because it ensures:
 * covering all connecting systems and/or partners
 * unambiguous translation of data from the CDM to the connecting data model and vice versa
 * less translating
 * separating of concerns  
 
<p align="center"> <b> Situation solved using a CDM </b></p>

<p align="center"> <img width="810" height="300" src="CDM.png"> </p>
