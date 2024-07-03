# PEI PowerSchool Main Customization Plugin

Catch-all for PEI-specific customizations that don't fit into a larger project.

## Summary of functionality

### Admin Portal

- **Enroll Student** - hides SSN and track, adds validate PEI Address button. DOES NOT add any fields that collect additional info - this has weird implications and should be avoided. Can lead to bad, bad things. We should generally avoid modifying this page.

#### Alerts

- **Alerts** - Add a PEI version of the PSSP Alert. A mutation observer in the student header wildcards modifies the real PSSP Alert to point to this page instead.

#### Contacts

- **Edit** - Remove gender field.

#### District Setup

- **School Info** - Add additional VP fields and school URL. Migrated these fields to u_def_ext_schools table.
  
#### PowerScheduler

- **Student Prefs** - Add Next Year Home Room

#### Staff Pages

- **Create Staff** - Adds staff mobile # and changes title to a dropdown (to support our use of School Messenger). Rmemoves some unused fields.
- **Edit Staff** - Largely similar changes as to Create Staff.

#### Student Pages

- **Addressess** 
    - Add a Validate a PEI Address button.
    - Add an archive of previous addresses.
  - **Demographics** 
    - Add legal name, indigenous self-identification, guardianship; removes or makes readonly a bunch of fields. Added the "Use legal name on report cards" option, and an listener to make the legal FIRST name required if that option is true. Legal last name not required, to account for students with no legal last name.
    - Add archive of previous addresses (visible on addesses page, home addresses only).
  - **Edit Transfer** - From Transfer Info screen, when you try to edit the current or previous enrollment record, removes Track.
  - **Emergency/Medical** - Removes existing allergy field/adds our custom allergy field. Removes emergency contact (use contacts instead) and immunization fields.
  - **Historical Grades** - Add credit totals for easier view.
  - **Modify Data** - Removes unused fields like lunch ID, track, house, team, campus. Adds Next Year Home Room, to make it more accessible.
  - **Other Information** - Removes some US-specific fields
- **Parents** - sets fields to read-only, so that duplicate contacts can't be created but any new contacts with original contact type set are displayed. Also, hiding this page hides the student email page, so this is a workaround.
- **Re-enrolments** - Remove track
- **Schedule Setup** - Add Next Year Home Room

### Public Portal

- **Scores and Teacher Comments pages** - All changes here so far are with the aim of removing unwanted access to report card comments via the portal.
- **Email notifications** - Made balance alert and additional email-addreses disabled.
- **Course Requests** - Hide counselor icon.
- **Term Grades** - Hide counselor icon.

### Power Teacher

- **Home page** - Adds the current cycle day in the upper right hand corner of the homepage. Removes silverware icon from PowerTeacher homepage. In version 22.5+ also removes the related header from the table.
- **Single Day Attendance** - Add Special Programs alert with PEI modifications.

#### Studentpages

- **Demographics** - adds student username and password (with toggle) to the demographics screen and removes some fields we don't use.
- **Student Services** - Adds Student Services page to Student Info pages. Available as an Initial Student Screen.

### Wildcards

- **teachers_title_student_end_css.pei_custom.student.alert.txt** - Adds 18+/Independent 18+ indicator, homeroom, student services pod to student header + mutation observer for Student Services Alert (teacher portal).
- **title_student_end_css.pei_custom.student.alert.txt (admin_student_header_details.pei_custom.student.alert.txt in EUI)** - Adds 18+/Independent 18+ indicator + mutation observer for Student Services Alert (admin portal).
- **title_student_end_css.pei_cutom.student.alert.txt (admin_student_header_details.pei_custom.stdent.information.txt in EUI)** - Adds homeroom and student services pod to student header.
- **guardian_header.pei_custom.leftnav.footer.txt** - Removes the teacher comments button from the public portal.
- **teachers_nav_css.pei_custom.leftnav.footer.txt** - Removes link to meal counts from navigation on Power Teacher home page.

## Pages with Direct Edits

(Full code in Other Files folder. Do not include in plug-in.)

- /admin/alerts/medicalalert.html - Inserted our allergies field.
- /teachers/powerteacher-pro/students/demo.html
    <!--Add Student Password -->
    <!-- Hide ethnicity-->
    <!-- Hide Area/Neighborhood-->

These files should be deleted with each upgrade, so that the latest stock file can load, and then we can re-apply changes, as necesary.

## Technical Debt
- *Done* Fix admin/schools/edit so that inputs point to u_def_ext_schools and not the dyn table. Migrate data from dyn to ext.
- *Done* Update all hardcoded text to message keys.
- Change medical alert to use mutation observer instead of direct edit.

## Change history
- **2024.6.1**: Added OPC Review page to admin and teacher portals (read-only for PT), and OPC Alert to students with approved OPCs.
- **2024.5.2**: Added Cycle Day to PowerTeacher homepage.
- **2024.5**: Migrated student header changes to student header wildcard.
- **2024.1.2**: Added legal name archiving and support for first-name-only legal names.
- **2024.1.1**: Updated for Enhanced UI and French translation.
- **1.2**: Fixed placement of Validate PEI Address button to uncouple it from the presence of a Google Maps validator; added modified Special Programs alert; added lines to translation files (among other edits); added access request to plugin.xml for CSP - installed in production on March 3, 2023 
- **1.1.2**: Fixed issue cause a second indigenous status and legal name field set to be created dynamically
- **1.1.1**: Fixed Edit Staff Information page to work with dropdown title
- **1.1.0**: Plugin reflects current state of production (September 2022)
