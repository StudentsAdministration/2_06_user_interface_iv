# Code for the create action
### Code added to the controller
````java    
  @GetMapping("/create")
  public   String   create(Model   model)   {
         model.addAttribute("student",   new   Student());  
         return   "create";
  }           
         
  

  @PostMapping("/create")
  public   String   create(@ModelAttribute   Student   stu)   {
         String   index   =   Integer.toString(students.size()   +   1);          stu.setStudentId(index);
         students.add(stu);
        return   "redirect:/";
 }

````   
### create.html
````java    
  <form   method="Post"   th:action="@{/create}"   th:object="${student}">         
         <input   type="text"   th:field="*{firstName}"   />
         <input   type="text"   th:field="*{lastName}"/>
         <input   type="date"   th:field="*{enrollmentDate}"/>
         <input   type="text"   th:field="*{cpr}"/>          
         <input   type="submit"   value="Send"   />
  </form>
```` 
### Student.java
````java    
//needed   for   input   field   on   html   pages   (in   order   to   serve   the   right format)

@DateTimeFormat(pattern   =   "yyyy-MM-dd") 
private   Date   enrollmentDate;

```` 


