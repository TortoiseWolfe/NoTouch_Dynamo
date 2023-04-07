# NoTouch_Dynamo

## 1. Create a new Class Library project in Visual Studio
   - Open Visual Studio
   - Click on "Create a new project"
   - Choose "Class Library (.NET Framework)"
   - Name the project and set the location
   - Click "Create"

## 2. Add Dynamo Core, Dynamo Visual Programming, and Revit API references
   - Right-click on "References" in the Solution Explorer
   - Click on "Add Reference"
   - Browse to the location of the required DLL files and add them:
     - Dynamo Core (DynamoCore.dll)
     - Dynamo Visual Programming (DynamoServices.dll)
     - Revit API (RevitAPI.dll and RevitAPIUI.dll)

## 3. Create custom namespace and classes for your nodes (HelloWorld and RevitWall)
   - In the Solution Explorer, right-click on the project and choose "Add" > "Class"
   - Name the class (e.g., HelloWorld.cs and RevitWall.cs) and click "Add"
   - Replace the default namespace and class declarations with your custom namespace and class names

## 4. Add constructors, fields, properties, and methods to the classes
   - In the HelloWorld class, add a private field, a public property, a default constructor, a parameterized constructor, and a method
   - In the RevitWall class, add a private constructor and a public static method

## 5. Utilize TransactionManager and wrap Revit elements using ToDSType() method
   - Add the required using directives to access TransactionManager, DocumentManager, and Revit.Elements
   - In the RevitWall class method, create a transaction using TransactionManager.Instance.EnsureInTransaction() and TransactionManager.Instance.TransactionTaskDone()
   - Wrap the Revit wall element using the ToDSType() method before returning it

## 6. Set the output path for the build
   - In Visual Studio, right-click on the project in the Solution Explorer and select "Properties"
   - Click on the "Build" tab
   - Set the "Output path" to the Dynamo packages folder (usually located at C:\Users\<username>\AppData\Roaming\Dynamo\Dynamo Revit\<version>\packages)

## 7. Compile the solution and create a DLL file
   - In Visual Studio, click on "Build" > "Build Solution"
   - The DLL file will be generated in the specified output path (Dynamo packages folder)

## 8. Launch Dynamo for Revit
   - Open Revit and create a new project or open an existing one
   - Go to the "Manage" tab and click on "Dynamo" to launch the Dynamo workspace

## 9. Test the custom nodes in Dynamo
   - In the Dynamo workspace, click on "Library" on the left side to view the available nodes
   - Find your custom nodes (HelloWorld and RevitWall) under the custom namespace you created (e.g., ZeroTouchNodes)
   - Drag and drop the custom nodes onto the workspace
   - Connect the required inputs to the nodes and run the Dynamo script to test their functionality
   - Verify that the custom nodes are working as expected (e.g., HelloWorld node outputs "Hello, World!" and RevitWall node creates a wall in Revit)
