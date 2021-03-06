JobJar: The multi-project todo management tool for people who don't like schedules and deadlines.

Origin
------
I have a lot of projects on the go, sometimes as many as a dozen at a time, each with a dozen or more todos required to get from start to finish. But I like the freedom to jump back and forth between projects, meandering my way through the forest of joblets, going where my whim of the day takes me, while still managing to push projects regularly onto the completed pile.

This system of time management works for me. It keeps me productive, keeps me creative, and despite the seeming chaos of my path through it all, projects keep getting finished. Novels, videos, software projects---they all sit on the stove, each getting stirred and seasoned according to my shifting moods, yet still all progressing steadily and getting realeased into the world as I finish with them.

Unfortunately, that's not how most people work, and it's definitely _not_ how most project management tools work. To most people, a project carries deadlines, commitments, and schedules, so for them, the need to track dates and timelines is crucial, which is reflected in the tools made for them. 

But what about we unshackled few who see our projects more like job-jars? Where's the tool that lets us keep track of _what_ is to be done, without having to also specify _when_ it should be done? What I wanted was a tool that would let me treat each project as a lists of steps, and then on each morning, pick a few from Column A and a few from Column B to make up my job list for the day.

Well, after trying almost a hundred different web sites, apps, and console tools, I finally gave in to the realization that there simply wasn't one out there that worked the way I do. 

So I built one.

Overview
--------
I call it JobJar, and it's pretty simple. For each project, I devise a simple tag-word to identify it. Then I tell JobJar the new project tag and give it jobs to add to that jar. Every morning I review a list of the jobs, organized by jar, and pick a few to do for the day. The day's list is easy to call up at any time through the day, and having that day-plan helps to keep me from wandering too far into the weeds.

About once a month, I review the jars themselves, and decide which ones I want to focus on for the coming month, and which I want to relegate to a back burner. By putting those deferred jars "to sleep," they don't show up in my daily review and I can focus my energies on the few strategic projects that are important, without ever losing track of the ones I'm leaving for later.

It's a combination of the principles of bullet journaling, and Getting Things Done, but stripped of all its calender tyrannies and then delivered on the command line, which is where I live.

Logging
-------
In addition to keeping track of jobs and projects, JobJar also keeps a running history. A sort of "Captain's Log." Every time you interact with a job, a timestamped note gets added to the log. Plus, you can add log notes of your own. These logs can later be reviewed as day reports, project reports, or any other way you might imagine sorting and filtering the log entries.

In practice, I find JobJar to be the ideal tool for my personal workflow. At the time I'm writing this document, the log reports are still in very crude summary form, but the job management tools are pretty solid now, and it's time to let others start playing with it. 

If you're looking for a stress-free way to plan your work, maybe JobJar is the tool you've been looking for.


Useage
------

   jj [options] stats  
   jj [options] projects  
   jj [options] add PROJ [JOBSTRING...]  
   jj [options] (list|picked|today|sleeping|started) [PROJ]  
   jj [options] (pick|unpick|start|finish) PROJ JOBID...  
   jj [options] delete PROJ [JOBID]  
   jj [options] report DATE [PROJ]  
   jj [options] log PROJ JOBID MESSAGE...  
   jj [options] sleep PROJ [JOBID...]  
   jj [options] wake PROJ [JOBID...]  
   jj -h | --help  
   jj -V | --version  

Options
-------
   -d      # Dump modified data file to STDOUT rather than saving to file  
   -a      # Report on ALL projects/tasks, including the sleeping ones  
   -D PATH # Look in directory at PATH for .job.jj and .log.jj files  
   -i N    # Show N digits of the job id (defuault = 2)  
   -w DT   # Log the current operation with date DT instead of today  
   -y      # Required extra confirmation for extreme commands like 'delete'  
   -v      # Display verbose output  
   -V      # Display version information  

Flags
-----

A task can have any combination of three status flags. Jobs can be created with these flags already set by prefixing the job description with any combination of these flags. (This is faster than creating the job and then running sleep/pick/start commands.) 

 - &ast; marks a task as started or in-progress  
 - ! marks a task as being picked for work today  
 - ~ marks a project or task as sleeping  

Sleeping projects and tasks are excluded from reports unless the -a option is present.

Job IDs
-------
Each job is given an id based on the MD5 hash of its text, so that log records and notes can be associated with it, but nobody has time to type in a 30-character string just to mark a job complete. So in practice, only the last 2 digits of the id string are shown in lists. This is usually sufficient to guarantee uniqueness, but on rare occasions, two jobs in a jar may have the same final digits. If this happens, just relist the jobs using the "-i" option to increase the number of digits of the id values shown.

If an operation specifies a target id that is ambiguous, the system will abort the operation and advise you to specify more digits of the id.

Files
-----
By default, JobJar looks at the user's home directory for two files: .jobs.jj and .log.jj. If those files exist in the current directory when jj is invoked, the local files will be used instead, and a note to that effect will be displayed in the output. I use this to keep my testing job list distinct from my _real_ list, but I imagine others might want to be able to keep their job jars more isolated.



Created 2018 by Jefferson Smith  
Check out my tools, videos, and novels at http://creativityhacker.ca
