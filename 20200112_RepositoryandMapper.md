@Repository
해당 클래스에서 발생하는 DB 관련 예외를 spring의 DAOException으로 전환
@Mapper
???


<h2>DAO 적용방식</h2>
3.2 Mapper interface 사용 방식
Mapper 인터페이스 작성 시 다음과 같이 @Mapper annotation 사용한다.

(패키지를 포함하는 클래스명 부분이 mapper xml 상의 namespace가 선택되고 인터페이스 메소드가 query id로 호출되는 방식)
``` java
@Mapper("employerMapper")
public interface EmployerMapper  {
 
    public List<EmpVO> selectEmployerList(EmpVO vo);
 
    public EmpVO selectEmployer(BigDecimal empNo);
 
    public void insertEmployer(EmpVO vo);
 
    public int updateEmployer(EmpVO vo);
 
    public int deleteEmployer(BigDecimal empNo);
 
}
```
이 경우는 xml 설정 상에 다음과 같은 MapperConfigurer 설정이 필요하다.

Ex: context-mapper.xml
``` xml
<bean class="egovframework.rte.psl.dataaccess.mapper.MapperConfigurer">
	<property name="basePackage" value="egovframework.rte.**.mapper" />
</bean>
basePackage에 지정된 패키지 안에서 @Mapper annotation을 스캔하는 설정이다.
```
⇒ @Mapper로 지정된 인터페이스를 @Service에서 injection 하여 사용함
``` java
public class EmployerMapperTest {
 
    @Resource(name = "employerMapper")
    EmployerMapper employerMapper;
 
@Test
    public void testInsert() throws Exception {
        EmpVO vo = makeVO();
 
        // insert
        employerMapper.insertEmployer(vo);
 
        // select
        EmpVO resultVO = employerMapper.selectEmployer(vo.getEmpNo());
 
        // check
        checkResult(vo, resultVO);
    }
 ```   
3.3 Annotation 사용 방식
mapper xml 작성 없이 Mapper 인터페이스 상에 @Select, @Insert, @Update, @Delete 등의 annotation을 통해 query가 지정되어 사용된다.

``` java
@Mapper("departmentMapper")
public interface DepartmentMapper  {
 
	@Select("select DEPT_NO as deptNo, DEPT_NAME as deptName, LOC as loc from DEPT where DEPT_NO = #{deptNo}")
    public DeptVO selectDepartment(BigDecimal deptNo);
 
	@Insert("insert into DEPT(DEPT_NO, DEPT_NAME, LOC) values (#{deptNo}, #{deptName}, #{loc})")
    public void insertDepartment(DeptVO vo);
 
	@Update("update DEPT set DEPT_NAME = #{deptName}, LOC = #{loc} WHERE DEPT_NO = #{deptNo}")
    public int updateDepartment(DeptVO vo);
 
	@Delete("delete from DEPT WHERE DEPT_NO = #{deptNo}")
    public int deleteDepartment(BigDecimal deptNo);
 
}
```
⇒ 이 경우는 별도의 mapper xml을 만들 필요는 없지만, dynamic query를 사용하지 못하는 등의 제약사항이 따름



출처: https://unabated.tistory.com/entry/mybatis-mapper-방식-적용 [랄라라]
