


# reference
* [一则线上MySql连接异常的排查过程](https://www.cnblogs.com/zhukunrong/p/4525955.html)
* [预编译语句(Prepared Statements)介绍，以MySQL为例](https://www.cnblogs.com/micrari/p/7112781.html)

```
Cause: com.mysql.jdbc.exceptions.jdbc4.MySQLNonTransientConnectionException: No operations allowed after connection closed.
; SQL []; No operations allowed after connection closed.; nested exception is com.mysql.jdbc.exceptions.jdbc4.MySQLNonTransientConnectionException: No operations allowed after connection closed.
	at org.springframework.jdbc.support.SQLExceptionSubclassTranslator.doTranslate(SQLExceptionSubclassTranslator.java:79)
	at org.springframework.jdbc.support.AbstractFallbackSQLExceptionTranslator.translate(AbstractFallbackSQLExceptionTranslator.java:73)
	at org.springframework.jdbc.support.AbstractFallbackSQLExceptionTranslator.translate(AbstractFallbackSQLExceptionTranslator.java:81)
	at org.mybatis.spring.MyBatisExceptionTranslator.translateExceptionIfPossible(MyBatisExceptionTranslator.java:75)
	at org.mybatis.spring.SqlSessionTemplate$SqlSessionInterceptor.invoke(SqlSessionTemplate.java:447)
	at com.sun.proxy.$Proxy43.selectOne(Unknown Source)
	at org.mybatis.spring.SqlSessionTemplate.selectOne(SqlSessionTemplate.java:167)
	... 91 more
Caused by: com.mysql.jdbc.exceptions.jdbc4.MySQLNonTransientConnectionException: No operations allowed after connection closed.
	at sun.reflect.NativeConstructorAccessorImpl.newInstance0(Native Method)
	at sun.reflect.NativeConstructorAccessorImpl.newInstance(NativeConstructorAccessorImpl.java:62)
	at sun.reflect.DelegatingConstructorAccessorImpl.newInstance(DelegatingConstructorAccessorImpl.java:45)
	at java.lang.reflect.Constructor.newInstance(Constructor.java:423)
	at com.mysql.jdbc.Util.handleNewInstance(Util.java:404)
	at com.mysql.jdbc.Util.getInstance(Util.java:387)
	at com.mysql.jdbc.SQLError.createSQLException(SQLError.java:917)
	at com.mysql.jdbc.SQLError.createSQLException(SQLError.java:896)
	at com.mysql.jdbc.SQLError.createSQLException(SQLError.java:885)
	at com.mysql.jdbc.SQLError.createSQLException(SQLError.java:860)
	at com.mysql.jdbc.ConnectionImpl.throwConnectionClosedException(ConnectionImpl.java:1246)
	at com.mysql.jdbc.ConnectionImpl.checkClosed(ConnectionImpl.java:1241)
	at com.mysql.jdbc.ConnectionImpl.prepareStatement(ConnectionImpl.java:4102)
	at com.mysql.jdbc.ConnectionImpl.prepareStatement(ConnectionImpl.java:4071)
	at sun.reflect.GeneratedMethodAccessor236.invoke(Unknown Source)
	at sun.reflect.DelegatingMethodAccessorImpl.invoke(DelegatingMethodAccessorImpl.java:43)
	at java.lang.reflect.Method.invoke(Method.java:498)
	at org.apache.tomcat.jdbc.pool.ProxyConnection.invoke(ProxyConnection.java:126)
	at org.apache.tomcat.jdbc.pool.JdbcInterceptor.invoke(JdbcInterceptor.java:108)
	at org.apache.tomcat.jdbc.pool.interceptor.AbstractCreateStatementInterceptor.invoke(AbstractCreateStatementInterceptor.java:66)
	at org.apache.tomcat.jdbc.pool.JdbcInterceptor.invoke(JdbcInterceptor.java:108)
	at org.apache.tomcat.jdbc.pool.interceptor.AbstractCreateStatementInterceptor.invoke(AbstractCreateStatementInterceptor.java:66)
	at org.apache.tomcat.jdbc.pool.JdbcInterceptor.invoke(JdbcInterceptor.java:108)
	at org.apache.tomcat.jdbc.pool.interceptor.AbstractCreateStatementInterceptor.invoke(AbstractCreateStatementInterceptor.java:66)
	at org.apache.tomcat.jdbc.pool.interceptor.ResetAbandonedTimer.invoke(ResetAbandonedTimer.java:60)
	at org.apache.tomcat.jdbc.pool.JdbcInterceptor.invoke(JdbcInterceptor.java:108)
	at org.apache.tomcat.jdbc.pool.interceptor.AbstractCreateStatementInterceptor.invoke(AbstractCreateStatementInterceptor.java:66)
	at org.apache.tomcat.jdbc.pool.JdbcInterceptor.invoke(JdbcInterceptor.java:108)
	at org.apache.tomcat.jdbc.pool.interceptor.AbstractCreateStatementInterceptor.invoke(AbstractCreateStatementInterceptor.java:66)
	at org.apache.tomcat.jdbc.pool.JdbcInterceptor.invoke(JdbcInterceptor.java:108)
	at org.apache.tomcat.jdbc.pool.interceptor.ConnectionState.invoke(ConnectionState.java:152)
	at org.apache.tomcat.jdbc.pool.JdbcInterceptor.invoke(JdbcInterceptor.java:108)
	at org.apache.tomcat.jdbc.pool.TrapException.invoke(TrapException.java:40)
	at org.apache.tomcat.jdbc.pool.JdbcInterceptor.invoke(JdbcInterceptor.java:108)
	at org.apache.tomcat.jdbc.pool.DisposableConnectionFacade.invoke(DisposableConnectionFacade.java:81)
	at com.sun.proxy.$Proxy120.prepareStatement(Unknown Source)
	at org.apache.ibatis.executor.statement.PreparedStatementHandler.instantiateStatement(PreparedStatementHandler.java:87)
	at org.apache.ibatis.executor.statement.BaseStatementHandler.prepare(BaseStatementHandler.java:88)
	at org.apache.ibatis.executor.statement.RoutingStatementHandler.prepare(RoutingStatementHandler.java:59)
	at org.apache.ibatis.executor.SimpleExecutor.prepareStatement(SimpleExecutor.java:85)
	at org.apache.ibatis.executor.SimpleExecutor.doQuery(SimpleExecutor.java:62)
	at org.apache.ibatis.executor.BaseExecutor.queryFromDatabase(BaseExecutor.java:325)
	at org.apache.ibatis.executor.BaseExecutor.query(BaseExecutor.java:156)
	at org.apache.ibatis.executor.CachingExecutor.query(CachingExecutor.java:109)
	at org.apache.ibatis.executor.CachingExecutor.query(CachingExecutor.java:83)
	at org.apache.ibatis.session.defaults.DefaultSqlSession.selectList(DefaultSqlSession.java:148)
	at org.apache.ibatis.session.defaults.DefaultSqlSession.selectList(DefaultSqlSession.java:141)
	at org.apache.ibatis.session.defaults.DefaultSqlSession.selectOne(DefaultSqlSession.java:77)
	at sun.reflect.GeneratedMethodAccessor233.invoke(Unknown Source)
	at sun.reflect.DelegatingMethodAccessorImpl.invoke(DelegatingMethodAccessorImpl.java:43)
	at java.lang.reflect.Method.invoke(Method.java:498)
	at org.mybatis.spring.SqlSessionTemplate$SqlSessionInterceptor.invoke(SqlSessionTemplate.java:434)
	... 93 more
Caused by: com.mysql.jdbc.exceptions.jdbc4.CommunicationsException: Communications link failure

The last packet successfully received from the server was 22,353 milliseconds ago.  The last packet sent successfully to the server was 6,231 milliseconds ago.
	at sun.reflect.NativeConstructorAccessorImpl.newInstance0(Native Method)
	at sun.reflect.NativeConstructorAccessorImpl.newInstance(NativeConstructorAccessorImpl.java:62)
	at sun.reflect.DelegatingConstructorAccessorImpl.newInstance(DelegatingConstructorAccessorImpl.java:45)
	at java.lang.reflect.Constructor.newInstance(Constructor.java:423)
	at com.mysql.jdbc.Util.handleNewInstance(Util.java:404)
	at com.mysql.jdbc.SQLError.createCommunicationsException(SQLError.java:988)
	at com.mysql.jdbc.MysqlIO.reuseAndReadPacket(MysqlIO.java:3552)
	at com.mysql.jdbc.MysqlIO.reuseAndReadPacket(MysqlIO.java:3452)
	at com.mysql.jdbc.MysqlIO.checkErrorPacket(MysqlIO.java:3893)
	at com.mysql.jdbc.MysqlIO.sendCommand(MysqlIO.java:2526)
	at com.mysql.jdbc.MysqlIO.sqlQueryDirect(MysqlIO.java:2673)
	at com.mysql.jdbc.ConnectionImpl.execSQL(ConnectionImpl.java:2549)
	at com.mysql.jdbc.PreparedStatement.executeInternal(PreparedStatement.java:1861)
	at com.mysql.jdbc.PreparedStatement.execute(PreparedStatement.java:1192)
	at sun.reflect.GeneratedMethodAccessor225.invoke(Unknown Source)
	at sun.reflect.DelegatingMethodAccessorImpl.invoke(DelegatingMethodAccessorImpl.java:43)
	at java.lang.reflect.Method.invoke(Method.java:498)
	at org.apache.tomcat.jdbc.pool.interceptor.AbstractQueryReport$StatementProxy.invoke(AbstractQueryReport.java:233)
	at com.sun.proxy.$Proxy121.execute(Unknown Source)
	at sun.reflect.GeneratedMethodAccessor225.invoke(Unknown Source)
	at sun.reflect.DelegatingMethodAccessorImpl.invoke(DelegatingMethodAccessorImpl.java:43)
	at java.lang.reflect.Method.invoke(Method.java:498)
	at org.apache.tomcat.jdbc.pool.interceptor.AbstractQueryReport$StatementProxy.invoke(AbstractQueryReport.java:233)
	at com.sun.proxy.$Proxy121.execute(Unknown Source)
	at sun.reflect.GeneratedMethodAccessor225.invoke(Unknown Source)
	at sun.reflect.DelegatingMethodAccessorImpl.invoke(DelegatingMethodAccessorImpl.java:43)
	at java.lang.reflect.Method.invoke(Method.java:498)
	at org.apache.tomcat.jdbc.pool.interceptor.AbstractQueryReport$StatementProxy.invoke(AbstractQueryReport.java:233)
	at com.sun.proxy.$Proxy121.execute(Unknown Source)
	at sun.reflect.GeneratedMethodAccessor225.invoke(Unknown Source)
	at sun.reflect.DelegatingMethodAccessorImpl.invoke(DelegatingMethodAccessorImpl.java:43)
	at java.lang.reflect.Method.invoke(Method.java:498)
	at org.apache.tomcat.jdbc.pool.interceptor.StatementDecoratorInterceptor$StatementProxy.invoke(StatementDecoratorInterceptor.java:249)
	at com.sun.proxy.$Proxy121.execute(Unknown Source)
	at org.apache.ibatis.executor.statement.PreparedStatementHandler.query(PreparedStatementHandler.java:63)
	at org.apache.ibatis.executor.statement.RoutingStatementHandler.query(RoutingStatementHandler.java:79)
	at org.apache.ibatis.executor.SimpleExecutor.doQuery(SimpleExecutor.java:63)
	at org.apache.ibatis.executor.BaseExecutor.queryFromDatabase(BaseExecutor.java:325)
	at org.apache.ibatis.executor.BaseExecutor.query(BaseExecutor.java:156)
	at org.apache.ibatis.executor.CachingExecutor.query(CachingExecutor.java:109)
	at org.apache.ibatis.executor.CachingExecutor.query(CachingExecutor.java:83)
	at org.apache.ibatis.session.defaults.DefaultSqlSession.selectList(DefaultSqlSession.java:148)
	at org.apache.ibatis.session.defaults.DefaultSqlSession.selectList(DefaultSqlSession.java:141)
	at org.apache.ibatis.session.defaults.DefaultSqlSession.selectOne(DefaultSqlSession.java:77)
	at sun.reflect.GeneratedMethodAccessor233.invoke(Unknown Source)
	at sun.reflect.DelegatingMethodAccessorImpl.invoke(DelegatingMethodAccessorImpl.java:43)
	at java.lang.reflect.Method.invoke(Method.java:498)
	at org.mybatis.spring.SqlSessionTemplate$SqlSessionInterceptor.invoke(SqlSessionTemplate.java:434)
	at com.sun.proxy.$Proxy43.selectOne(Unknown Source)
	at org.mybatis.spring.SqlSessionTemplate.selectOne(SqlSessionTemplate.java:167)
	at sun.reflect.GeneratedMethodAccessor233.invoke(Unknown Source)
	at sun.reflect.DelegatingMethodAccessorImpl.invoke(DelegatingMethodAccessorImpl.java:43)
	at java.lang.reflect.Method.invoke(Method.java:498)
	at com.chinaredstar.perseus.db.DynamicSqlSessionTemplate$SqlSessionInterceptor.invoke(DynamicSqlSessionTemplate.java:83)
	at com.sun.proxy.$Proxy43.selectOne(Unknown Source)
	at com.chinaredstar.perseus.db.DynamicSqlSessionTemplate.selectOne(DynamicSqlSessionTemplate.java:100)
	at org.apache.ibatis.binding.MapperMethod.execute(MapperMethod.java:75)
	at org.apache.ibatis.binding.MapperProxy.invoke(MapperProxy.java:53)
	at com.sun.proxy.$Proxy101.countDeliverOrders(Unknown Source)
	at com.chinaredstar.ordercenter.external.shop.ExternalShopService.getShopToDoList(ExternalShopService.java:58)
	at com.chinaredstar.ordercenter.external.shop.ExternalShopService$$FastClassBySpringCGLIB$$458930ff.invoke(<generated>)
	at org.springframework.cglib.proxy.MethodProxy.invoke(MethodProxy.java:204)
	at org.springframework.aop.framework.CglibAopProxy$CglibMethodInvocation.invokeJoinpoint(CglibAopProxy.java:720)
	at org.springframework.aop.framework.ReflectiveMethodInvocation.proceed(ReflectiveMethodInvocation.java:157)
	at org.springframework.aop.aspectj.MethodInvocationProceedingJoinPoint.proceed(MethodInvocationProceedingJoinPoint.java:85)
	at com.chinaredstar.ordercenter.aop.ExternalExceptionInterceptor.intercept(ExternalExceptionInterceptor.java:24)
	at sun.reflect.GeneratedMethodAccessor286.invoke(Unknown Source)
	at sun.reflect.DelegatingMethodAccessorImpl.invoke(DelegatingMethodAccessorImpl.java:43)
	at java.lang.reflect.Method.invoke(Method.java:498)
	at org.springframework.aop.aspectj.AbstractAspectJAdvice.invokeAdviceMethodWithGivenArgs(AbstractAspectJAdvice.java:620)
	at org.springframework.aop.aspectj.AbstractAspectJAdvice.invokeAdviceMethod(AbstractAspectJAdvice.java:609)
	at org.springframework.aop.aspectj.AspectJAroundAdvice.invoke(AspectJAroundAdvice.java:68)
	at org.springframework.aop.framework.ReflectiveMethodInvocation.proceed(ReflectiveMethodInvocation.java:179)
	at org.springframework.aop.interceptor.ExposeInvocationInterceptor.invoke(ExposeInvocationInterceptor.java:92)
	at org.springframework.aop.framework.ReflectiveMethodInvocation.proceed(ReflectiveMethodInvocation.java:179)
	at org.springframework.aop.framework.CglibAopProxy$DynamicAdvisedInterceptor.intercept(CglibAopProxy.java:655)
	at com.chinaredstar.ordercenter.external.shop.ExternalShopService$$EnhancerBySpringCGLIB$$b30cc2fe.getShopToDoList(<generated>)
	at com.alibaba.dubbo.common.bytecode.Wrapper60.invokeMethod(Wrapper60.java)
	... 27 more
Caused by: java.net.SocketException: Connection timed out
	at java.net.SocketInputStream.socketRead0(Native Method)
	at java.net.SocketInputStream.socketRead(SocketInputStream.java:116)
	at java.net.SocketInputStream.read(SocketInputStream.java:170)
	at java.net.SocketInputStream.read(SocketInputStream.java:141)
	at com.mysql.jdbc.util.ReadAheadInputStream.fill(ReadAheadInputStream.java:101)
	at com.mysql.jdbc.util.ReadAheadInputStream.readFromUnderlyingStreamIfNecessary(ReadAheadInputStream.java:144)
	at com.mysql.jdbc.util.ReadAheadInputStream.read(ReadAheadInputStream.java:174)
	at com.mysql.jdbc.MysqlIO.readFully(MysqlIO.java:3001)
	at com.mysql.jdbc.MysqlIO.reuseAndReadPacket(MysqlIO.java:3462)
	... 98
```