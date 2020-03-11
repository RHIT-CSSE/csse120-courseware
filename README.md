# csse120-public 
# RepoHelper

------------------------------------------------------------------------
This folder contains scripts to help maintain student repositories.

The scripts work for any course that uses a structure for student
repositories that is similar to that used by CSSE 120.

Author:  David Mutchler, based on work by Mike McLeish and Micah Taylor.
------------------------------------------------------------------------

------------------------------------------------------------------------
To use the scripts:
------------------------------------------------------------------------

IMPORTANT: Run these scripts on campus or through the Rose-Hulman VPN.
   Even STARTING to run them off-campus without the VPN
   may LOCK YOU OUT of the ability to run them for a period of time.

   This appears to be because (it seems that) Rose-Hulman enables
   some sort of lock when an off-campus user attempts to access
   a server repeatedly over a short period of time.

   I have NOT had any trouble accessing   gitter   through PyCharm
   off-campus (even with no VPN).  It seems that only repeated access
   over a short period of time (ala these scripts) causes problems.

------------------------------------------------------------------------
Step 1. At the beginning of the term:
------------------------------------------------------------------------

   Step 1a:
      Edit   SET_COURSE_AND_TERM

      to specify the term and course for which you want to make/maintain
      student repositories, plus your username for running SSH on gitter.

      Note: If you are using these scripts for more than one course in
      a given term, you will need to do Step 1a each time you want to
      switch from one course to the other.

   Step 1b:
      Run    SCRIPT-0a-make-folders

      This script makes folders named like this:
         REPOS/REPOS-csse120-202030
         DATA/DATA-csse120-202030

   Step 1c:
      Visit the Schedule Lookup pages for the sections of your course.
      From those pages, use the  Download Roster  button to download
      the course rosters (CSV files) for the sections of your course,
      putting the downloaded CSV files into the   DATA/DATA-XXX-XXX
      folder for your course and term.

   Step 1d:
      Run   SCRIPT-0b-make-usernames

      This script will extract the student usernames into files
         students-01    students-02    etc
      for the sections.
      Then it makes a   students   file that contains the concatenation
      of the   students-XX   files.

      This script will NOT overwrite existing, non-empty files.
      Instead, it shows a DIFF of the existing file
       and the extracted usernames.

   Step 1e:
      Add usernames to the other files in the DATA/DATA-XXX-XXX folder:
         instructors
         assistants
         others
         temp  (commonly used for testing prior to a "production" run)

      Add other files as you choose.
      Adjust usernames in all the files as desired.

      Subsequent scripts will use whichever files in DATA/DATA-XXX-XXX
      that you specify in the scripts.

   Step 1f:
      Create a file   DEFAULT-RIGHTS   in the DATA/DATA-XXX-XXX folder.
      In that file, list the usernames to whom you want to give
      full access to the repositories to be created in the next step.

------------------------------------------------------------------------
Step 2. At the beginning of the term, and whenever you want to add
        a new repository for a student (or student team):
------------------------------------------------------------------------

   Step 2:
      Run   SCRIPT-1-make-and-initialize-new-repos

      Note: The above script exits if a failure occurs.
         If this happens and you don't care (but want to continue
         with the rest of the above script), just comment-out
         the offending lines in the above script.

      Note: There appears to be a BUG that:
         Trying to give an additional user rights to a repository
         after the repository "owner" has pushed changes appears
         to fail.

------------------------------------------------------------------------
Thereafter, you can run:
   SCRIPT-pull-repos     to update all the repositories
   SCRIPT-add-project    to add a project to all of the repositories

In each of the above, you can change the   username_files  variable
(that is set near the beginning of the script) if you want to perform
the action to some (not all) of the repositories.

For SCRIPT-add-project, set the   folder_to_populate   variable
(that is set near the beginning of the script) to the folder you want
to populate into the repositories.
------------------------------------------------------------------------
