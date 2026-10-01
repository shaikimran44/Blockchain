Description
                    
                    


FixItNow, a home appliance repair company, needs a
    system to track the repair status of service requests. Each service request is
    assigned a unique Request ID, and the system must allow technicians to add
    repair details and retrieve current repair statuses based on this ID. Develop a
    Java program to help the company effectively manage and monitor these records.



Functional Requirements


    
        
            
                Req.#
            
            
                Requirement Description
            
            
                Method Name
            
            
                Parameters
            
            
                Description
            
        
    
    
        
            
                1
            
            
                Add a repair request record to the system
            
            
                addRepairRequests
            
            
                String requestId, String repairStatus
            
            
                This method adds a new requestId and its corresponding repairStatus to
                    a HashMap named repairMap. 
                Note: Key = requestId, Value = repairStatus.
            
        
        
            
                2
            
            
                Retrieve the repair status for a specific request
            
            
                retrieveRepairStatus
            
            
                String requestId
            
            
                The method retrieves the status of the repair. Returns "The
                        repair status is <repairStatus> for the request id <requestId>"
                    if found. Otherwise, returns "The request id <requestId> does
                        not exist".Condition: The requestId is case-sensitive.This method should return a String.
            
        
    


 

You are provided with the main method as a code template, and it is excluded from evaluation.

Note:


    Edit only the RequestSystem class to implement the business
            requirements. 
    The methods and the constructor
            should be public, and the attributes of the class should be private. 
    In the sample input/output
            provided, the highlighted text in bold corresponds to the input given by
            the user and the rest of the text represents the output. 
    Ensure that the names for
            classes, attributes, and methods are provided as specified in the question
            description. 
    Please do not use
            System.exit(0); to terminate the program. 


 

Sample Input and Output 1:

Enter the number of repair request records to be added
    3
    Enter the repair records (Request Id: Repair Status)
    RQ100:Fixed
        RQ101:Awaiting Parts
        RQ102:Scheduled
    Enter the request Id to find its repair status
    RQ101
    The repair status is Awaiting Parts for the request id RQ101


 

Sample Input and Output 2:

Enter the number of repair request records to be added
    2
    Enter the repair records (Request Id: Repair Status)
    RQ200:In Progress
        RQ201:Cancelled
    Enter the request Id to find its repair status
    RQ999
    The request id RQ999 does not exist 
    So their is two java files 1.UserInterface.java : //The main method in UserInterface class is not evaluated. USe to test your code.
    //The expected business logic is called in the main.
    //Make sure that same method signature is implemented.
    2.RequestSystem.java :
    import java.util.HashMap;
    import java.util.Map;
    public class RequestSystem {
    Map<String, String> requireMap = new HashMap<>();
    public Map<String,string> getRepairMap(){
    return repairMap;
    }
    public void setRepairMap(Map<String,String> repairMap){
    this.repairMap = repairMap;
    }
    //write and implement  the business requirements
    }
