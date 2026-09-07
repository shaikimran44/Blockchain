Description
                    
                    

In a vehicle management system, every vehicle must be validated before it is added to the registry. The application will validate vehicle details based on predefined criteria. Develop a program to validate and register vehicles based on their details.

Functional Requirements:
 
    
        
            
                
                    Req.#
                
                  Requirements Description  
                
                 Type (Class)
                
                    Method Name
                
                
                    Parameters
                
                
                    Description
                
            
            
                
                    1
                
                  Include a four-argument constructor in Vehicle class.
                
                 Vehicle
                 The getter-setter methods for all the attributes and no-argument constructor are provided as part of code skeleton
                
                 String vehicleId, String vehicleType, String fuelType, int engineCapacity
                
                 Include a public four-argument constructor in Vehicle class by following the order mentioned : vehicleId, vehicleType, fuelType, and engineCapacity
                
            
            
                 2
                 Include a one-argument constructor in InvalidVehicleException class
                 InvalidVehicleException
                 -
                String message
                Include a public one argument constructor to set the message string to the super class.
            
            
                
                    3
                
                
                    Extract the details of the Vehicle, verify the details, and create an object for the Vehicle class.
                
                 Vehicle
                
                    validateVehicleDetails
                
                
                     String vehicleDetails
                
                 This method is tasked with validating and parsing a string representing vehicle details. It takes in the string details, splits this string into an array of strings using the colon ( : ) as a delimiter.
                    It proceeds to check whether each part of the vehicle details conforms to certain patterns:
                    
                    
                        
                            The vehicleId must match the pattern "VH/" followed by exactly 4 digits.
                            The vehicleType must match one of the predefined categories: "Car", "Bike", or "Bus".
                            The fuelType must match either "Petrol", "Diesel", or "Electric".
                            The engineCapacity must be greater than 50 and less than or equal to 5000.
                        
                    
                    If all parts of the details pass the validation, it constructs a Vehicle object using the parsed details and returns it. However, if any part of the details fails the validation, it throws an InvalidVehicleException with an error message "Invalid vehicle details"
                        indicating that the vehicle details are invalid.
                    
                    Constraints
                    
                    
                        The method should return the Object of type Vehicle.
                        vehicleType and fuelType is case-sensitive.
                    
                    
                    
                
            
        
    

    You are provided with the main method in the UserInterface class as a code template, and it is excluded from evaluation.



    Note:
    
        Edit only the Vehicle and InvalidVehicleException classes to implement the business requirements.
        The methods and the constructor should be public, and the attributes of the class should be private.
        In the Sample Input / Output provided, the highlighted text in bold corresponds to the input given by the user and the rest of the text represents the output.
        Ensure that the names for classes, attributes, and methods are provided as specified in the question description.
        Please do not use System.exit(0); to terminate the program.
    


Input Format:  <vehicleId>: <vehicleType>: <fuelType>: <engineCapacity>

Sample Input / Output 1

    
    
        
            Enter the Vehicle DetailsVH/1234:Car:Petrol:1600Vehicle DetailsVehicle ID: VH/1234Vehicle Type: CarFuel Type: PetrolEngine Capacity: 1600 cc
        
    
    
      
    Sample Input / Output 2 
    
    
        
            Enter the Vehicle DetailsVH/12:Truck:CNG:50Invalid vehicle details it has 3 java 1.InvalidVehicleException.java where it has public class InvalidVehicleException extends exception {
            //include one argument constructor with string message and set this message to super class constructor
            } 2.UserInterface.java and 3.Vehicle.java where //include four argument Constructor and //write and implement the business requirements
