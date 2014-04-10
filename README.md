openshift-jrebel-cartridge
=================================

####This only works on non-scaled gears at the moment
####This cartridge is tested as working with the following cartridges on OpenShift Online 
- jbossews-1.0 (Tomcat 6)
- jbossews-2.0 (Tomcat 7)
- jbossas-7 (JBoss AS 7)

The following examples will use the jbossews-2.0 (Tomcat 7) cartridge, but you can use any of the supported cartridges with a slight modification to the directions below.  

Create your application using the tomcat 7 (jbossews-2.0) cartridge

	rhc app create tomcat7 jbossews-2.0
	
Then upload your jrebel.lic file to your OPENSHIFT_DATA_DIR

	rhc scp tomcat7 upload jrebel.lic app-root/data
    
Then install this cartridge

    rhc cartridge-add https://raw.github.com/developercorey/openshift-jrebel-cartridge/master/metadata/manifest.yml -a <appname>
    
Then restart your application

	rhc app restart tomcat7
	
Now clone your application to your workstation (using either your IDE or git command line), then add the rebel.xml and rebel-remote.xml files and configure them to point to your application url (http://app-domain.rhcloud.com).  
You then need to do a "git add", "git commit", and "git push" to get these files onto your gear so that you can use JRebel.  
Now you can use your favorite IDE with the JRebel plugin installed to update your application without having to do a git push  
If you are using IntelliJ, remember that this is a maven based project, so you will have to finagle the Web module settings a little and move 
    
Please log any issues to the git repository issue tracker
