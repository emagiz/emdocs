# eMagiz as a HIP

| point to point | many to many | 
| :------------: | :----------: | 
| <img width="1200" height="70" src="/img/ILM/point-to-point.png"> | <img width="1200" height="240" src="/img/ILM/more-many-to-many.png"> |  

In the first image you can see a stand-alone message flow represented by a **point-to-point connection** (one integration). When there are more integrations needed the effectiveness of single message flows decreases. A situation like the one in the second image which represents a **many-to-many connection** cannot be solved by only using stand-alone message flows in an effective way.  
This is where a [CDM](https://en.wikipedia.org/wiki/Canonical_model "Canonical Data Model") - canonical (common) data model is very useful because it ensures:
 * covering all connecting systems and/or partners
 * unambiguous translation of data from the [CDM](https://en.wikipedia.org/wiki/Canonical_model "Canonical Data Model") to the system data model and vice versa
 * less translations
 * separation of concerns  
 
<p align="center"> <b> Situation solved using a CDM</b></p>

<p align="center"> <img width="810" height="300" src="/img/ILM/CDM.png"> </p>
