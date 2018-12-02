# utl-dropping-down-to-R-from-sas-and-creating-a-box-plot
Dropping down to R from sas and creating a box plot

    Dropping down to R from sas and creating a box plot

    Output graph
    https://tinyurl.com/yc8tjwcb
    https://github.com/rogerjdeangelis/utl-dropping-down-to-R-from-sas-and-creating-a-box-plot/blob/master/utl-dropping-down-to-R-from-sas-and-creating-a-box-plot

    github
    https://tinyurl.com/y9y8hs4o
    https://github.com/rogerjdeangelis/utl-dropping-down-to-R-from-sas-and-creating-a-box-plot

    StackOverflow
    https://tinyurl.com/y8smvo82
    https://stackoverflow.com/questions/53544459/rlang-graphs-in-sas-with-r-script-vanishes


    INPUT
    =====

    SD1.HAVE total obs=428

      MAKE     MODEL                        MPG_CITY

      Acura    MDX                             17
      Acura    RSX Type S 2dr                  24
      Acura    TSX 4dr                         22
      Acura    TL 4dr                          20
      Acura    3.5 RL 4dr                      18
      Acura    3.5 RL w/Navigation 4dr         18
      Acura    NSX coupe 2dr manual S          17
      ...


    EXAMPLE OUTPUT (see high res png ABOVE)
    ---------------------------------------

    This was created by command macro unv

              MP_CITY

       Value     #     Boxplot

       61+       1        *
         .       1        *
         .
         .
         .
       51+
         .
         .       1        *
         .
         .
       41+
         .       1        *
         .       1        *
         .       2        0
         .       8        0
       31+       1        0
         .      12        0
         .      23        |
         .      31        |
         .      25        |
       21+      95     +--+--+
         .     106     *-----*
         .      72     +-----+
         .      30        |
         .      16        |
       11+       2        0


    PROCESS
    =======

    %utl_submit_r64('
    library(haven);
    have<-read_sas("d:/sd1/have.sas7bdat");
    png(file="d:/png/utl-dropping-down-to-R-from-sas-and-creating-a-box-plot.png");
    boxplot(have$MPG_CITY);
    png();
    ');

    OUTPUT

    see above

    *                _               _       _
     _ __ ___   __ _| | _____     __| | __ _| |_ __ _
    | '_ ` _ \ / _` | |/ / _ \   / _` |/ _` | __/ _` |
    | | | | | | (_| |   <  __/  | (_| | (_| | || (_| |
    |_| |_| |_|\__,_|_|\_\___|   \__,_|\__,_|\__\__,_|

    ;

    options validvarname=upcase;
    libname sd1 "d:/sd1";
    data sd1.have(keep=make model mpg_city);
      set sashelp.cars;
    run;quit;


