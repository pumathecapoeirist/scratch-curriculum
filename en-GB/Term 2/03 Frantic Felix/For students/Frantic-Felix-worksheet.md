￼



##TASK 1: Collision detectors
``` scratch
when 'flag' clicked
forever
	go to Felix
	if <color [] is touching [] ?>
		set blocked right to 1
	else
	set block right to 0
	end if
end forever
```
At the moment, Felix just needs a script to follow the mouse pointer forever. 

￼￼4. The final thing to do is __falling__. If there’s no solid ground under Felix, we want him to fall. That’s another

forever
	if <<key left arrow pressed?> and (blocked left)=0>
		point in direction -90
		move two steps
	end if
	if <<key right arrow pressed?> and (blocked right)=0>
		point in direction 90
		move two steps
	end if

forever if <<key left arrow pressed?>or<key right arrow pressed?>>
	next costume
	wait 0.1 secs
end if

when FLAG clicked (handle falling)
forever
	if <blocked bottom=0>
		change by -2
	end if
end forever




when FLAG clicked (handle falling)
forever
	if <height to jump=0>
		if blocked top=1
			set height to jump to 0
		else
			change y by 10
			change height to jump by -10
		end if
	else
		if <blocked bottom=0>
			change by -2
		end if
	end if
end forever


when FLAG clicked
go to x:-50 y:47
point in direction -90
forever
	if <touching Felix?>
		broadcast lose
	end if
	if x position > -200
		point in direction 90
	end if
	if x position > -50
		point in direction -90
	end if
	move 2 steps
end forever








```scratch
when I receive [start level]
go to x:(item 'current level' of [xs])y:(item `current level` of [ys])
point in direction (item `current level` of [directions])
show
forever
	if <<key[left arrow]pressed?>and `blocked left`=[0]>
		point in direction -90
		move 2 steps
	end if
	if <<key[right arrow]pressed?>and `blocked right`=[0]>
		point in direction 90
		move 2 steps
	end if
	if <<key[space]pressed?>and `blocked bottom`=[1]>
		set [height to jump]to[100]
	end if
end forever
```



set [current level] to 1
broadcast [start level]

when I receive [start level]
go to x:(item current level of [xs])y:(item current level of [ys])
forever
	if <if keys to get = 0>
	change [color]effect by [25]
		if <touching [Felix]?>
			if <current level = `length of [keys per level]>
				say [You win!]
				broadcast [win]
				stop all
			else
				change [current level] by 1
				broadcast [start level]
			end if
		end if
	end if
end forever

