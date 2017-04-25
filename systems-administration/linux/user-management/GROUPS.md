Groups
======

#### Create Group

	groupadd group_name            # create group
	cut -d: -f1 /etc/group | sort  # list all groups sorted by name

#### Add User to Group

	usermod -G [GROUPNAME] [USERNAME]        # adds user to group or changes current group
	usermod -G [GROUP1],[GROUP2] [USERNAME]  # adds user to two groups
	usermod -a  -G [GROUP] [USERNAME]        # adds user to group in addition to current group
	groups                                   # prints out current users group
