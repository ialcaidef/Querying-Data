# Querying-Data
20487_MOD02_DEMO_L3

# Lesson 3: Querying Data

### Demonstration: Using Language-Integrated Query (LINQ) to Entities

1. Open the Command Prompt window.

2. To change the directory to the starter project, at the command prompt, run the following command:

   ```bash
    cd [Repository Root]\Allfiles\Mod02\DemoFiles\UsingLINQtoEntities\Starter
   ```

3. To restore all the dependencies and tools of a project, at the command prompt, run the following command:

   ```base
    dotnet restore
   ```

4. To open the project in VS Code, paste the following command, and then press Enter:

   ```bash
    code .
   ```

5. On the **Explorer** blade, under **STARTER**, double-click **Program.cs**.

6. To create a new **SchoolContext** object, append the following code to the **Main** method:

   ```cs
    using (var context = new SchoolContext())
    {
    }
   ```

    To control the release of unmanaged resources used by the context, such as a database connection, use the **using** statement.

7. To create the database, add the following code in the **using** block:

   ```cs
    DbInitializer.Initialize(context);
   ```

8. To select all the courses from the database, in the **using** block under **DBInitializer**, add the following LINQ to the **Entities** code:

   ```cs
    var courses = from c in context.Courses
                  select c;
   ```

9. To print the courses and students list to the console window, in the **using** block after the LINQ to the **Entities** code, add the following code:

   ```cs
    foreach (var course in courses)
    {
        Console.WriteLine($"Course: {course.Name}");
        foreach (var student in course.Students)
        {
            Console.WriteLine($"\t Student name: {student.Name}");
        }
    }
    Console.ReadLine();
   ```

10. To run the application, in command prompt, run the following command:

    ```bash
    dotnet run
    ```

11. In the console window, review the course and student lists printed to the console window.

12. To stop the application, in the command prompt press Ctrl+C.

13. Close all open windows.

### Demonstration 2: Running Stored Procedures with Entity Framework

#### Demonstration Steps

1. Open the Command Prompt window.

2. To change the directory to the starter project, at the command prompt, run the following command:

   ```bash
    cd [Repository Root]\AllFiles\Mod02\DemoFiles\StoredProcedure
   ```

3. To restore all dependencies and tools of a project, at the command prompt, run the following command:

   ```base
    dotnet restore
   ```

4. To open the project in VS Code, paste the following command, and then press Enter:

   ```bash
    code .
   ```

5. On the **Explorer** blade, under **STARTER**, double-click **Program.cs**.

6. Navigate to the **Main** method, and notice that a **SchoolContext** instance is created to establish a connection to the database.

7. Review the query that is being assigned to the *averageGradeInCourse* variable. Notice that the average grade of the **ASP.NET Core** course is calculated, and then printed to the console.

8. The **ExecuteSqlCommand** statement calls the **spUpdateGrades** stored procedure with two parameters, **CourseName** and **GradeChange**.

9. To run the application, in command prompt, run the following command:

   ```bash
   dotnet run
   ```

   >**Note**: Notice that the updated average grade is printed to the console before and after the change.

10. To stop the application, in the command prompt press Ctrl+C.

11. Close all open windows.
