# ProblemSet2

// Requirement 8(a) : Place the class in the required package. 
package edu.monmouth.problemSet2;

import edu.monmouth.campusvehicle.CampusVehicle;

public class ProblemSet2 {

	public static void main(String[] args) {
		
		
		System.out.println("PROBLEM SET 2");
		System.out.println("CAMPUS VEHICLE TESTING");
		
		// Requirements 8(B) - 8(f): Test the default constructor and mutators. 
		System.out.println("\nTEST 1: DEFAULT CONSTRUCTOR");
		
		
		//8(b): Create an object using the default constructor. 
		CampusVehicle vehicle1 = new CampusVehicle();
		
		//8(c): Immediately retrieve and print all attributes. 
		printAttributes(vehicle1);
		
		System.out.println("\nSetting valid values:");
		
		//8(d): Set valid values using the three mutators.
		vehicle1.setId("MU1234");
		vehicle1.setLocation("Library");
		vehicle1.setAvailable(true);
		
		//8(e): Retrieve and print the updated attributes.
		printAttributes(vehicle1);
		
		//8(f): Test Checkout, returnVehicle, and isAvailable
		testCheckoutReturn(vehicle1);
		
		// 8(g) - 8(k): Test the constructor with parameters.
		
		System.out.println("\nTest 2: CONSTRUCTOR WITH PARAMETERS");
		
		//8(g): Create an object with valid values 
		// for all three attributes. 
		
		CampusVehicle vehicle2 = new CampusVehicle("MU2026", "University Bluffs", false);
		
		//8(h): Immediately retrieve and print all attributes. 
		printAttributes(vehicle2);
		
		System.out.println("\nChanging attributes:");
		
		//Requirement 8(i): Set the specific values requested. 
		vehicle2.setId("MU1090");
		vehicle2.setLocation("library");
		vehicle2.setAvailable(true);
		
		//8(j): Retrieve and print the updated attributes.
		printAttributes(vehicle2);
		
		//8(k): Test Checkout, returnVehicle, and isAvailable.
		testCheckoutReturn(vehicle2);
		
		//8(l) : Create objects with invalid IDs or locations.
		//For each object, print all attributes and test checkout,
		//For each object, print all attributes and test checkout, 
		//RETURNvEHICLE, and isAvailable
		//Test a null ID.
		System.out.println("\nTEST 3: NULL ID");
		
		CampusVehicle vehicle3 = new CampusVehicle(null, "Library", true);
		
		printAttributes(vehicle3);
		testCheckoutReturn(vehicle3);
		
		// Test an empty ID.
		System.out.println("\nTEST 4: EMPTY ID");
		CampusVehicle vehicle4 = new CampusVehicle("", "Parking Lot", true);
		
		printAttributes(vehicle4);
		testCheckoutReturn(vehicle4);
		
		// Test an ID with fewer than 4 characters. 
		// This vehicle also starts unavailable.
		System.out.println("\nTest 5: SHORT ID");
		CampusVehicle vehicle5 = new CampusVehicle("MU1", "Spruce Hall", false);
		
		printAttributes(vehicle5);
		testCheckoutReturn(vehicle5);
		
		//Test an Id with more than 12 characters 
		System.out.println("\nTEST 6: LONG ID");
		
		CampusVehicle vehicle6 = new CampusVehicle("MU12345678901", "laurel Hall", true);
		
		printAttributes(vehicle6);
		testCheckoutReturn(vehicle6);
		
		//Test an ID that does not start with MU.
		System.out.println("\nTEST 7: INVALID ID PREFIX");
		
		CampusVehicle vehicle7 = new CampusVehicle("AB1234", "University Bluffs", true);
		
		printAttributes(vehicle7);
		testCheckoutReturn(vehicle7);
		
		// Test a null location. 
		System.out.println("\nTEST 8: NULL LOCATION");
		
		CampusVehicle vehicle8 = new CampusVehicle("MU2001",null, true);
		
		printAttributes(vehicle8);
		testCheckoutReturn(vehicle8);
		
		//Test an empty location
		System.out.println("\nTEST 9: EMPTY LOCATION");
		
		CampusVehicle vehicle9 = new CampusVehicle("MU2002","", true);
		
		printAttributes(vehicle9);
		testCheckoutReturn(vehicle9);
		
		// Test a location that is not one of the five permitted locations.
		System.out.println("\nTEST 10: 	INVALID LOCATION");
		
		CampusVehicle vehicle10 = new CampusVehicle("MU2003","Walmart", true);
		
		printAttributes(vehicle10);
		testCheckoutReturn(vehicle10);
		
		//Additional check for requirement 7: case and valid boundary lengths. 
		// Accept valid Strings regardless of capitalization. 
		
		System.out.println("\nTEST 11: CASE INSENSITIVITY");
		CampusVehicle vehicle11 = new CampusVehicle("mu1234","lIbRaRy", true);
		
		printAttributes(vehicle11);
		testCheckoutReturn(vehicle11);
		
		//Additional boundary check for Requirement 2:
		// Accept an ID with exactly 4 characters.
		System.out.println("\nTEST 12: VALID ID LENGTH:4");
		CampusVehicle vehicle12 = new CampusVehicle("MU12","Parking Lot", true);
		
		printAttributes(vehicle12);
		testCheckoutReturn(vehicle12);
		
		//Additional boundary check for Requirement 2:
		//Accept an ID with exactly 12 characters.
		System.out.println("\nTEST 13: VALID ID LENGTH:12");
		CampusVehicle vehicle13 = new CampusVehicle("MU1234567890","laurel Hall", true);
		
		printAttributes(vehicle13);
		testCheckoutReturn(vehicle13);
		
		System.out.println("\nAll TESTS COMPLETED");		
	}
    
	//Helper method: retrieve and display all three vehicle attributes. 
	public static void printAttributes(CampusVehicle vehicle) {
		System.out.println("ID: " + vehicle.getId());
		System.out.println("Location: " + vehicle.getLocation());
		System.out.println("Available: " + vehicle.isAvailable());		
	}
	//Helper method for Requirement 8(f), 8(k), and 8(l):
	//Test checkout and returnVehicle, checking availability after each. 
	public static void testCheckoutReturn(CampusVehicle vehicle) {
		
		//Display the initial availability. 
		System.out.println("Before checkout: " + vehicle.isAvailable());
		
		//Check out the vehicle and display its availability. 
		vehicle.checkout();
		
		System.out.println("After checkout: " + vehicle.isAvailable());
		
		// Additional check for Requirement 6: an unavailable vehicle must remain unavailable. 
		vehicle.checkout();
		
		System.out.println("After second checkout: " + vehicle.isAvailable());
		
		// Return the vehicle and display its availability. 
		vehicle.returnVehicle();
		
		System.out.println("After returnVehicle: " + vehicle.isAvailable());
		
	}
}
