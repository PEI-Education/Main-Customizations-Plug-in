# PEI PowerSchool Main Customization Plugin

Catch-all for PEI-specific customizations that don't fit into a larger project.

## Summary of functionality

### Admin Portal

- **Enroll Student** - hides SSN and track, adds validate PEI Address button. DOES NOT add any fields that collect additional info - this has weird implications and should be avoided. Can lead to bad, bad things. We should generally avoid modifying this page.

#### Contacts

- **Edit** - Remove gender field.

#### District Setup

- **School Info** - Add additional VP fields and school URL

### PowerScheduler

- **Student Prefs** - Add Next Year Home Room

#### Staff Pages

- **Create Staff** - Adds staff mobile # and changes title to a dropdown (to support our use of School Messenger). Rmemoves some unused fields.
- **Edit Staff** - Largely similar changes as to Create Staff.

#### Student Pages

- **Addressess** - Add a Validate a PEI Address button.
- **Demographics** - Add legal name, indigenous self-identification, guardianship; removes or makes readonly a bunch of fields.
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

### Power Teacher

- **Home page** - Removes silverware icon from PowerTeacher homepage. In version 22.5+ also removes the related header from the table.

#### Studentpages

- **Demographics** - adds student username and password (with toggle) to the demographics screen and removes some fields we don't use.
- **Student Services** - Adds Student Services page to Student Info pages. Available as an Initial Student Screen.

### Wildcards

- **title_student_end_css.pei_custom.student.alert.txt** - Adds 18+/Independent 18+ indicator to student header.
- **guardian_header.pei_custom.leftnav.footer.txt** - Removes the teacher comments button from the public portal.
- **teachers_nav_css.pei_custom.leftnav.footer.txt** - Removes link to meal counts from navigation on Power Teacher home page.

## Pages with Direct Edits

(Full code in Other Files folder. Do not include in plug-in.)

- /admin/alerts/medicalalert.html - Inserted our allergies field.
- /teachers/powerteacher-pro/students/demo.html
    <!--Add Student Password -->
    <!-- Hide ethnicity
    <!-- Hide Area/Neighborhood

These files should be deleted with each upgrade, so that the latest stock file can load, and then we can re-apply changes, as necesary.

## Version history

- **1.1.1**: Fixed Edit Staff Information page to work with dropdown title
- **1.1.0**: Plugin reflects current state of production
