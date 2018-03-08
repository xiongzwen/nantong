oracle连接数
--查看进程数，超过300重启61上的SM服务，用户名：sys  密码：oracle ，连接方式SYSDBA
select COUNT(*) FROM v$process;  
select count(*) from v$session;

--查看是否有锁表情况
SELECT object_name, machine, s.sid, s.serial#
FROM gv$locked_object l, dba_objects o ,gv$session s
WHERE l.object_id = o.object_id
AND l.session_id = s.sid;

--杀死锁表会话进程
--alter system kill session 'sid, serial#';
