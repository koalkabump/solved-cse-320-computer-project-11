Download Link: https://assignmentchef.com/product/solved-cse-320-computer-project-11
<br>
<h1>Assignment Overview</h1>




This assignment develops familiarity with data structures in assembly language.  You will develop a set of ARM assembly language functions to complete a program which manages statistics for a basketball team.




It is worth 50 points (5% of course grade) and must be completed no later than 11:59 PM on Thursday, 12/5.




<h1>Assignment Deliverables</h1>




The deliverables for this assignment are the following files:




proj11.makefile – the makefile which produces “proj11” proj11.support.s – the source code for your support module




Be sure to use the specified file names and to submit them for grading via the CSE handin system.




<h1>Assignment Specifications</h1>




The program will use an ordered table to maintain the data set, where each player’s jersey number will serve as a unique key to identify that player.  The capacity of the ordered table will be determined when it is created.




<ol>

 <li>The instructor-supplied driver module (function “main” and associated functions) will manage the overall operation of the program and will perform all input and output operations.</li>

</ol>




<ol start="2">

 <li>You will supply the functions whose declarations are listed below:</li>

</ol>




int search( struct table*, unsigned long, struct player** ); int delete( struct table*, unsigned long );

int insert( struct table*, unsigned long, char*, int, int, int, int );




Those three functions (and any “helper” functions which you develop) will constitute a module named “proj11.support.s”.




<h1>Assignment Notes</h1>




<ol>

 <li>The functions in your support module must be hand-written ARM assembly language functions (you may not submit compiler-generated assembly language functions).</li>

</ol>




<ol start="2">

 <li>The file “project11.support.h” (appended below) includes all relevant declarations, along with descriptive comments.</li>

</ol>




<ol start="3">

 <li>The file “project11.driver.o” contains the instructor-supplied driver module.</li>

</ol>




<ol start="4">

 <li>The file “project11.data” contains a sample data set (the statistics for the MSU Women’s Basketball team during the 2018-2019 season). Your program must function correctly for that sample data set, as well as any other properly formatted data set.</li>

</ol>




<ol start="5">

 <li>You may wish to create stubs for the required functions, then translate, link and execute the program to explore the behavior of the driver module.  /***********************************************************************/</li>

</ol>

/*  Declarations for Project #11                                       */

/***********************************************************************/




struct player

{

unsigned short number;    /* player’s jersey number (key)   */   char name[25];            /* player’s name                  */   unsigned short games;     /* number of games played         */   unsigned short bask2;     /* number of 2-point baskets made */   unsigned short bask3;     /* number of 3-point baskets made */   unsigned short free;      /* number of free throws made     */   unsigned short points;    /* total points scored            */   float points_per_game;    /* points per game played         */

};

struct table

{

unsigned short capacity;  /* number of elements in table    */   unsigned short count;     /* number of players in table     */   struct player* memory;    /* pointer to array of players    */

};




/***********************************************************************/

/*  Function:  search                                                  */

/*                                                                     */

/*  Purpose:  locate and return a pointer to a player, if the          */

/*  player is present in the table.                                    */

/*                                                                     */

/*  Arguments:                                                         */

/*    pointer to table of players                                      */

/*    jersey number of player to be located                            */

/*    pointer to pointer to player                                     */

/*                                                                     */

/*  Return value:                                                      */

/*    1 (true) if player located, 0 (false) otherwise                  */

/***********************************************************************/




int search( struct table*, unsigned long, struct player** );




/***********************************************************************/

/*  Function:  delete                                                  */

/*                                                                     */

/*  Purpose:  delete a player from the table, if the                   */

/*  player is present in the table.                                    */

/*                                                                     */

/*  Arguments:                                                         */

/*    pointer to table of players                                      */

/*    jersey number of player to be deleted                            */

/*                                                                     */

/*  Return value:                                                      */

/*    1 (true) if player deleted, 0 (false) otherwise                  */

/***********************************************************************/




int delete( struct table*, unsigned long ); /***********************************************************************/

/*  Function:  insert                                                  */

/*                                                                     */

/*  Purpose:  insert a player into the table, as long as there is      */

/*  room in the table and the player is not already present.           */

/*                                                                     */

/*  Arguments:                                                         */

/*    pointer to table of players                                      */

/*    jersey number of player to be inserted                           */

/*    pointer to name of player                                        */

/*    number of games played                                           */

/*    number of 2-point baskets made                                   */

/*    number of 3-point baskets made                                   */

/*    number of free throws made                                       */

/*                                                                     */

/*  Return value:                                                      */

/*    1 (true) if player inserted, 0 (false) otherwise                 */

/***********************************************************************/




int insert( struct table*, unsigned long, char*, int, int, int, int );