#IN Vs EXISTS

The two are processed quite differently.

##IN Clause

	Select * from T1 where x in ( select y from T2 )

is typically processed as:

	select *
	from t1, ( select distinct y from t2 ) t2
	where t1.x = t2.y;

The sub query is evaluated, distinct, indexed and then
joined to the original table -- typically.

##As opposed to "EXIST" clause

	select * from t1 where exists ( select null from t2 where y = x )

That is processed more like:

	for x in ( select * from t1 )
	loop
	if ( exists ( select null from t2 where y = x.x )
	then
	OUTPUT THE RECORD
	end if
	end loop

It always results in a full scan of T1 whereas the first query can make use of
an index on T1(x).


##So, when is exists appropriate and in appropriate?

Lets say the result of the subquery
	( select y from T2 )

is "huge" and takes a long time. But the table T1 is relatively small and
executing ( select null from t2 where y = x.x ) is fast (nice index on
t2(y)). Then the exists will be faster as the time to full scan T1 and do the
index probe into T2 could be less then the time to simply full scan T2 to build
the subquery we need to distinct on.

Lets say the result of the subquery is small -- then IN is typicaly more
appropriate.

If both the subquery and the outer table are huge -- either might work as well
as the other -- depends on the indexes and other factors. 
