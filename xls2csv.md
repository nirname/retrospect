# XLS to CSV

    sudo yum install perl
    sudo yum install perl-CPAN

    sudo perl -MCPAN -e 'shell'
      install CPAN
      reload CPAN
      install YAML
      # from here
      install Locale::Recode
      install Unicode::Map
      install Spreadsheet::ParseExcel
      install Spreadsheet::ParseExcel::FmtUnicode
      install Text::CSV_XS
    exit

    wget http://search.cpan.org/CPAN/authors/id/K/KE/KEN/xls2csv-1.06.tar.gz

    tar zxpfv xls2csv-1.06.tar.gz
    cd xls2csv-1.06

    perl Makefile.PL
    make
    make test
    make install
