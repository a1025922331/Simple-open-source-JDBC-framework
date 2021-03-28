# Simple-open-source-JDBC-framework

// JDBC框架类
public class JDBCTemplate {
	//通过有参构造为数据源赋值
    public JDBCTemplate(DataSource dataSource) {}
	
	//查询方法：用于将一条记录封装成自定义对象并返回
	public <T> T queryForObject(String sql, ResultSetHandler<T> rsh,Object...objs) {}
	
	//查询方法：用于将多条记录封装成自定义对象并添加到集合返回
	public <T> List<T> queryForList(String sql, ResultSetHandler<T> rsh, Object...objs) {}
	
	//查询方法：用于将聚合函数的查询结果进行返回
	public Long queryForScalar(String sql, ResultSetHandler<Long> rsh, Object...objs) {}
	
	//用于执行增删改功能的方法
	public int update(String sql,Object...objs) {}
	
 }
 
// 用于处理结果集方式的接口
public interface ResultSetHandler<T> {
	//resultSet处理方法
    <T> T handler(ResultSet rs);
}

// 实现类1：用于将查询到的一条记录，封装为Student对象并返回
public class BeanHandler<T> implements ResultSetHandler<T>{
	// 重写handler方法。用于将一条记录封装到自定义对象中
	public T handler(ResultSet rs) {}
}

// 实现类2：用于将查询到的多条记录，封装为Student对象并添加到集合返回
public class BeanListHandler<T> implements ResultSetHandler<T>{
	// 重写handler方法。用于将多条记录封装到自定义对象中并添加到集合返回
	public List<T> handler(ResultSet rs) {}
}

// 实现类3：用于将聚合函数的查询结果返回
public class ScalarHandler<T> implements ResultSetHandler<T> {
	//2.重写handler方法
	public Long handler(ResultSet rs) {}
}
