.dockerignore cheats
====================

(May be out of date, uses pre Docker Compose versions)

#### .dockerignore file ex:

	*/temp*      - excludes any file starting with temp in any dir below root
	*/*/temp*    - excludes any file starting with temp two levels below root
	temp?        - excludes files matching the pattern (ex. tempa, tempb)
	*.md         - excludes all markdown files in the root dir
	!LICENSE.md  - an exception to the exclusion (must be after the exclusion rule)
	



