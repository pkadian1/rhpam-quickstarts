# rhpam-quickstarts
Red Hat PAM use cases quickstarts
 RHPAM - 7.11.1
 Java - JDK 11
 


Payload ---


{ "userdetails": {
        "Person": {
            "name": "khd",
            "id": "989"
   }},
 "addressdetails": {
    "AddressDetails": {
      "address_details": [
        {
          "com.epgs.custom_rest_payload.Address": {
            "pincode": "12103",
            "district": "JJR"
          }
        },
       {
          "com.epgs.custom_rest_payload.Address": {
            "pincode": "124507",
            "district": "Bgarh"
          }
        }
      ]
    }
  }
 }


Iterate----


System.out.println("mphdetails ================ Apan"+ userdetails.getName() +"service request id"+userdetails.getId());



org.json.JSONObject myobj=new org.json.JSONObject();
myobj.put("name",userdetails.getName());
myobj.put("id",userdetails.getId());
System.out.println("mphdetails ================ Object"+ myobj.toString()); 


java.util.List<com.epgs.custom_rest_payload.Address> myList = new java.util.ArrayList<com.epgs.custom_rest_payload.Address>();
myList=addressdetails.getAddress_details();

java.util.List<Object> addressdetail = new java.util.ArrayList<>();

for(com.epgs.custom_rest_payload.Address addr :myList) {
System.out.println("============ district"+addr.getDistrict());
org.json.JSONObject addrobj=new org.json.JSONObject();
addrobj.put("addressId",addr.getDistrict());
addrobj.put("addressId1",addr.getPincode());
System.out.println("addrdetails ================ Object"+ addrobj.toString()); 
addressdetail.add(addrobj);
}
System.out.println("addrdetails ================ Object"+ addressdetail); 


 output------
 
 13:04:32,906 INFO  [stdout] (default task-180) mphdetails ================ Apankhdservice request id989
13:04:32,907 INFO  [stdout] (default task-180) mphdetails ================ Object{"name":"khd","id":989}
13:04:32,907 INFO  [stdout] (default task-180) ============ districtJJR
13:04:32,908 INFO  [stdout] (default task-180) addrdetails ================ Object{"addressId1":12103,"addressId":"JJR"}
13:04:32,908 INFO  [stdout] (default task-180) ============ districtBgarh
13:04:32,908 INFO  [stdout] (default task-180) addrdetails ================ Object{"addressId1":124507,"addressId":"Bgarh"}
13:04:32,908 INFO  [stdout] (default task-180) addrdetails ================ Object[{"addressId1":12103,"addressId":"JJR"}, {"addressId1":124507,"addressId":"Bgarh"}]











