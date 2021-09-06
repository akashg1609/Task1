# Task1
package UserData;

import java.net.StandardSocketOptions;
import java.util.Collections;
import java.util.List;
import java.util.Random;
import java.util.stream.Collectors;
import java.util.stream.Stream;

class UserPersonalDetails {
    public String Name;
    public String Age;
    public String Location;
    public String PG;
    public String Hostel;
    public String Phone_Number;
    public Address Address;
    public String Password;

    public String getPassword(String Name, String Age, String Phone_Number){
        Random random = new Random();
        String  GeneratedPassword = Name.subSequence(0,4)+""
                +Phone_Number.subSequence(5,10);
        Stream<Character> PasswordStream =
                GeneratedPassword.codePoints().mapToObj(c -> (char) c);
        List<Character> PasswordList = PasswordStream.collect(Collectors.toList());
        Collections.shuffle(PasswordList);
        String Password = PasswordList.stream()
                .collect(StringBuilder::new, StringBuilder::append, StringBuilder::append)
                .toString();
        System.out.println(Password);
        return Password;

    }

    public void UserPersonalDefinetion(String Name, String age, String Location, String PG , String Hostel , String Phone_Number,Address Address ) {
        this.Name=Name;
        this.Age=Age;
        this.Location=Location;
        this.PG=PG;
        this.Hostel=Hostel;
        this.Phone_Number=Phone_Number;
        this.Address= Address;
        this.Password=getPassword(Name,Age,Phone_Number);
    }

    public String getName() {
        return Name;
    }

    public String getAge() {
        return Age;
    }

    public String Location() {
        return Location;
    }

    public String getPG() {
        return PG;
    }
    public String getHostel() {
        return Hostel;
    }
    public String getPhone_Number() {
        return Phone_Number;
    }

    public String FullAddress() {

        return new StringBuilder().append("Name ")
                .append(Name+",").append("Age "+Age).append(", ").append(Phone_Number).append(", ").toString();
    }

}
class Address{
    private String Name;
    private String Age;
    private String ZipCode;
    public Address(String Name,String Age,String ZipCode){
        this.Name = Name;
        this.Age =  Age;
        this.ZipCode = ZipCode;
    }

    public String getZip() {
        return ""+Name+" ,"+Age+" ,"+ZipCode+".";
    }
}
