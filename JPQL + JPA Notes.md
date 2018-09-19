### JPQL + JPA Notes

#### HIBERNATE(Framework) + JPA 连接 database flow
*	`persistence.xml` 用`<class>project_path_to_file<class>` 来告诉Hibernate 要读取哪几个file
* `<class>project_path_to_file<class>` 里面
	* `@Table(name = "table1" , uniqueConstraints = @UniqueConstraint(columnNames = {"id"}))`
	* table1就是数据库里面的table1 这样就把这个class和table1链接了

#### JPQL中的NativeQuery vs NamedQuery区别
* `NamedNativeQuery` 就是直接database的sql就可以 用的`variable` 都是`relative to 在数据库中的table1`
* `NamedQuery`按照 JPA的syntax来 用的`variable`都是`relative to class_a`自己

		@NamedNativeQuery(name = "query_name",
			query="SELECT * FROM table1 where emp_id IS NULL"
			)
	   VS		
	
		@NamedQuery(name = "query_name1", query="SELECT emp FROM Employee emp WHERE emp.Id IS NULL" ),

