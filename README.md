# UAb_patientHealthRisk

[![Replit Ready to Run](https://img.shields.io/badge/OCaml-Ready_to_Try-informational?logo=ocaml&labelColor=white&color=orange)](https://try.ocamlpro.com/#code/%28*'!*'File:'efolioA.ml'!*!*'UC:'Linguagens'de'Programa%c3%a7%c3%a3o!*!*'by'Diogo'Ant%c3%a3o!*'03/04/2021!*%29!!open'Printf!!%28*'defini%c3%a7%c3%a3o'de'uma'enum'para'o'tipo'de'dados'$%28risco$%28'*%29!type'risco'='Alto'$5'Medio'$5'Baixo'$5'Desconhecido'$5'Inconclusivo!!%28*'defini%c3%a7%c3%a3o'de'um'record'para'o'tipo'de'dados'$%28senior$%28'*%29!type'senior'='$4!nutente':'int;!ndoencas':'int;!nmedicamentos':'int;!acidente':'bool;!doenca':'bool;!sozinho':'bool;!autonomia':'bool;!desportoj':'bool;!autofisica':'bool;!fisica':'bool;!profissaorisco':'risco!$6!!%28*'defini%c3%a7%c3%a3o'do'n%c3%bamero'de'factos'para'cada'senior'*%29!let'n_factos'='11!!%28*'defini%c3%a7%c3%a3o'do'ficheiro'de'input'*%29!%28*'let'file'='$%28data/factos.txt$%28'*%29!!%28*'data'*%29!let'input'='$/'$%28123456700;3;4;n;s;n;n;n;n;n;medio$%28;!$%28123456701;2;3;n;n;n;n;n;n;n;medio$%28;!$%28123456702;2;3;n;n;n;n;n;n;n;baixo$%28;!$%28123456709;0;1;n;n;n;n;n;n;s;baixo$%28;!$%28123456800;4;9;s;n;s;s;s;s;s;medio$%28;!$%28123456801;4;4;s;s;n;s;s;s;s;baixo$%28;!$%28123456802;2;5;s;s;n;s;s;s;s;baixo$%28;!$%28123456803;2;5;s;esta;linha;esta;errada$%28'$1;;!!%28*'fun%c3%a7%c3%a3o'para'leitura'de'dados'a'partir'de'um'ficheiro;'%c3%a9'criada'uma'lista'de'strings'*%29!let'read_lines'filename'=!if'Sys.file_exists'filename'then!begin!let'in_ch'='open_in'filename'in!let'try_read'%28%29'=!try'Some'%28input_line'in_ch%29'with'End_of_file'-$.'None'in!let'rec'loop'lines_list'='match'try_read'%28%29'with!$5'Some'str'-$.'loop'%28str'::'lines_list%29!$5'None'-$.'close_in'in_ch;'List.rev'lines_list'in!loop'$/$1!end!else'$/$1;;!!!%28*'fun%c3%a7%c3%a3o'que'converte'uma'string'num'bool'*%29!let'my_bool_of_string'str'='match'str'with!$5'$%28s$%28'-$.'true!$5'$%28S$%28'-$.'true!$5'$%28n$%28'-$.'false!$5'$%28N$%28'-$.'false!$5'_'''-$.'false;;!!!%28*'fun%c3%a7%c3%a3o'que'converte'uma'string'num'tipo'de'risco'*%29!let'risco_of_string'str'='match'str'with!$5'$%28alto$%28''-$.'Alto!$5'$%28medio$%28'-$.'Medio!$5'$%28baixo$%28'-$.'Baixo!$5'_'''''''-$.'Desconhecido;;!!!%28*'fun%c3%a7%c3%a3o'que'converte'um'tipo'de'risco'numa'string'*%29!let'string_of_risco'r'='match'r'with!$5'Alto''-$.'$%28Alto$%28!$5'Medio'-$.'$%28Medio$%28!$5'Baixo'-$.'$%28Baixo$%28!$5'_'''''-$.'$%28Inconclusivo$%28;;!!!%28*'fun%c3%a7%c3%a3o'que'cria'uma'lista'de'listas'de'strings'a'partir'de'uma'lista'de'strings'*%29!let'create_list_list'str_l'=!%28*'A'fun%c3%a7%c3%a3o'split'cria'uma'lista'de'strings'a'partir'de'uma'string'$%28cortando$%28'esta'%c3%baltima'sempre'que'encontra'o'carater'$,;$,'*%29!let'split'line'='String.split_on_char'$,;$,'line'in!List.map'split'str_l;;!!!%28*'fun%c3%a7%c3%a3o'que'filtra'uma'lista'de'listas'consoante'a'dimensao'de'cada'lista'interior'*%29!let'filter_list_by_dim'll'=!let'verifica_n_campos'lista_interior'='if'List.length'lista_interior'='n_factos'then'true'else'false'in!List.filter'verifica_n_campos'll;;!!!%28*'fun%c3%a7%c3%a3o'que'cria'uma'lista'de'seniores'a'partir'de'uma'lista'de'listas'de'strings'*%29!let'create_senior_list'll'=!%28*'A'fun%c3%a7%c3%a3o'senior_of_list'converte'uma'lista'de'strings'num'senior'*%29!let'senior_of_list'l'='$4!nutente'='int_of_string'%28List.nth'l'0%29;!ndoencas'='int_of_string'%28List.nth'l'1%29;!nmedicamentos'='int_of_string'%28List.nth'l'2%29;!acidente'='my_bool_of_string'%28List.nth'l'3%29;!doenca'='my_bool_of_string'%28List.nth'l'4%29;!sozinho'='my_bool_of_string'%28List.nth'l'5%29;!autonomia'='my_bool_of_string'%28List.nth'l'6%29;!desportoj'='my_bool_of_string'%28List.nth'l'7%29;!autofisica'='my_bool_of_string'%28List.nth'l'8%29;!fisica'='my_bool_of_string'%28List.nth'l'9%29;!profissaorisco'='risco_of_string'%28List.nth'l'10%29!$6!in!List.map'senior_of_list'll;;!!!%28*'fun%c3%a7%c3%a3o'que'cria'uma'lista'de'riscos'a'partir'de'uma'lista'de'seniores'*%29!%28*'a'lista'de'riscos'tem'exatamente'a'mesma'dimens%c3%a3o'e'ordem'da'lista'de'seniores'*%29!let'create_risco_list'sl'=!%28*'A'fun%c3%a7%c3%a3o'decide_risco'decide'qual'o'grau'de'risco'correspondente'a'cada'senior'*%29!let'decide_risco's'='match's'with!$5'$4!ndoencas;!nmedicamentos;!doenca'='true;!autonomia'='false;!autofisica'='false;!profissaorisco!$6'when'ndoencas'$.'2'&&'nmedicamentos'$.'3'&&'%28profissaorisco'='Alto'$5$5'profissaorisco'='Medio%29'-$.'Alto!$5'$4!ndoencas;!nmedicamentos;!desportoj'='false;!fisica'='false;!profissaorisco!$6'when'ndoencas'$-='2'&&'nmedicamentos'$-='3'&&'%28profissaorisco'='Medio'$5$5'profissaorisco'='Baixo%29'-$.'Medio!$5'$4!nmedicamentos;!acidente'='false;!doenca'='false;!sozinho'='false;!profissaorisco'='Baixo!$6'when'nmedicamentos'$-='2'-$.'Baixo!$5'_'-$.'Inconclusivo!in!List.map'decide_risco'sl;;!!!%28*'fun%c3%a7%c3%b5es'para'impress%c3%a3o'de'uma'tabela'na'consola'*%29!let'print_aster'%28%29'='printf'$%28**********************************$0n$%28;;!let'print_header'%28%29'='printf'$%28*''''Utente'''''*''''''Risco'''''*$0n$%28;;!!!%28*'fun%c3%a7%c3%a3o'que'toma'como'argumentos'um'senior'e'um'risco'a'ele'associado'e'imprime'na'consola'o'n%c3%bamero'de'utente'do'senior'e'qual'o'respetivo'grau'de'risco'*%29!let'print_risco's'r'='printf'$%28*''$+10d'''*''$+12s''*$0n$%28's.nutente'%28string_of_risco'r%29;;!!!%28*'fun%c3%a7%c3%a3o'que'itera'conjuntamente'a'lista'de'seniores'e'a'lista'de'riscos'associada'e'chama'a'fun%c3%a7%c3%a3o'print_risco'a'cada'itera%c3%a7%c3%a3o'*%29!let'print_all'rl'sl'=!let'f's'r'='print_risco'r's'in!List.iter2'f'rl'sl;;!!!!%28*'fun%c3%a7%c3%a3o'principal'que'executa'de'facto'o'programa'*%29!let'main'=!%28*'let'm_string_list'='read_lines'file'in'*%29!let'm_string_list'='input'in!let'm_list_list'='create_list_list'm_string_list'in!let'm_filtered_list'='filter_list_by_dim'm_list_list'in!let'm_senior_list'='create_senior_list'm_filtered_list'in!let'm_risco_list'='create_risco_list'm_senior_list'in!begin!print_aster'%28%29;!print_header'%28%29;!print_aster'%28%29;!print_all'm_risco_list'm_senior_list;!print_aster'%28%29!end;;)

[EN] This project was made under the Curricular Unit of **Programming Languages** in the Computer Science and Engineering Bachelor Program of Universidade Aberta, academic year of 2020-21.

[PT] Este projeto foi realizado no âmbito da Unidade Curricular de **Linguagens de Programação** da Licenciatura em Engenharia Informática da Universidade Aberta no ano letivo de 2020-21.

## Compile
	ocamlc -o main main.ml
	
## Try OCaml
Try it [here](https://try.ocamlpro.com/#code/%28*'!*'File:'efolioA.ml'!*!*'UC:'Linguagens'de'Programa%c3%a7%c3%a3o!*!*'by'Diogo'Ant%c3%a3o!*'03/04/2021!*%29!!open'Printf!!%28*'defini%c3%a7%c3%a3o'de'uma'enum'para'o'tipo'de'dados'$%28risco$%28'*%29!type'risco'='Alto'$5'Medio'$5'Baixo'$5'Desconhecido'$5'Inconclusivo!!%28*'defini%c3%a7%c3%a3o'de'um'record'para'o'tipo'de'dados'$%28senior$%28'*%29!type'senior'='$4!nutente':'int;!ndoencas':'int;!nmedicamentos':'int;!acidente':'bool;!doenca':'bool;!sozinho':'bool;!autonomia':'bool;!desportoj':'bool;!autofisica':'bool;!fisica':'bool;!profissaorisco':'risco!$6!!%28*'defini%c3%a7%c3%a3o'do'n%c3%bamero'de'factos'para'cada'senior'*%29!let'n_factos'='11!!%28*'defini%c3%a7%c3%a3o'do'ficheiro'de'input'*%29!%28*'let'file'='$%28data/factos.txt$%28'*%29!!%28*'data'*%29!let'input'='$/'$%28123456700;3;4;n;s;n;n;n;n;n;medio$%28;!$%28123456701;2;3;n;n;n;n;n;n;n;medio$%28;!$%28123456702;2;3;n;n;n;n;n;n;n;baixo$%28;!$%28123456709;0;1;n;n;n;n;n;n;s;baixo$%28;!$%28123456800;4;9;s;n;s;s;s;s;s;medio$%28;!$%28123456801;4;4;s;s;n;s;s;s;s;baixo$%28;!$%28123456802;2;5;s;s;n;s;s;s;s;baixo$%28;!$%28123456803;2;5;s;esta;linha;esta;errada$%28'$1;;!!%28*'fun%c3%a7%c3%a3o'para'leitura'de'dados'a'partir'de'um'ficheiro;'%c3%a9'criada'uma'lista'de'strings'*%29!let'read_lines'filename'=!if'Sys.file_exists'filename'then!begin!let'in_ch'='open_in'filename'in!let'try_read'%28%29'=!try'Some'%28input_line'in_ch%29'with'End_of_file'-$.'None'in!let'rec'loop'lines_list'='match'try_read'%28%29'with!$5'Some'str'-$.'loop'%28str'::'lines_list%29!$5'None'-$.'close_in'in_ch;'List.rev'lines_list'in!loop'$/$1!end!else'$/$1;;!!!%28*'fun%c3%a7%c3%a3o'que'converte'uma'string'num'bool'*%29!let'my_bool_of_string'str'='match'str'with!$5'$%28s$%28'-$.'true!$5'$%28S$%28'-$.'true!$5'$%28n$%28'-$.'false!$5'$%28N$%28'-$.'false!$5'_'''-$.'false;;!!!%28*'fun%c3%a7%c3%a3o'que'converte'uma'string'num'tipo'de'risco'*%29!let'risco_of_string'str'='match'str'with!$5'$%28alto$%28''-$.'Alto!$5'$%28medio$%28'-$.'Medio!$5'$%28baixo$%28'-$.'Baixo!$5'_'''''''-$.'Desconhecido;;!!!%28*'fun%c3%a7%c3%a3o'que'converte'um'tipo'de'risco'numa'string'*%29!let'string_of_risco'r'='match'r'with!$5'Alto''-$.'$%28Alto$%28!$5'Medio'-$.'$%28Medio$%28!$5'Baixo'-$.'$%28Baixo$%28!$5'_'''''-$.'$%28Inconclusivo$%28;;!!!%28*'fun%c3%a7%c3%a3o'que'cria'uma'lista'de'listas'de'strings'a'partir'de'uma'lista'de'strings'*%29!let'create_list_list'str_l'=!%28*'A'fun%c3%a7%c3%a3o'split'cria'uma'lista'de'strings'a'partir'de'uma'string'$%28cortando$%28'esta'%c3%baltima'sempre'que'encontra'o'carater'$,;$,'*%29!let'split'line'='String.split_on_char'$,;$,'line'in!List.map'split'str_l;;!!!%28*'fun%c3%a7%c3%a3o'que'filtra'uma'lista'de'listas'consoante'a'dimensao'de'cada'lista'interior'*%29!let'filter_list_by_dim'll'=!let'verifica_n_campos'lista_interior'='if'List.length'lista_interior'='n_factos'then'true'else'false'in!List.filter'verifica_n_campos'll;;!!!%28*'fun%c3%a7%c3%a3o'que'cria'uma'lista'de'seniores'a'partir'de'uma'lista'de'listas'de'strings'*%29!let'create_senior_list'll'=!%28*'A'fun%c3%a7%c3%a3o'senior_of_list'converte'uma'lista'de'strings'num'senior'*%29!let'senior_of_list'l'='$4!nutente'='int_of_string'%28List.nth'l'0%29;!ndoencas'='int_of_string'%28List.nth'l'1%29;!nmedicamentos'='int_of_string'%28List.nth'l'2%29;!acidente'='my_bool_of_string'%28List.nth'l'3%29;!doenca'='my_bool_of_string'%28List.nth'l'4%29;!sozinho'='my_bool_of_string'%28List.nth'l'5%29;!autonomia'='my_bool_of_string'%28List.nth'l'6%29;!desportoj'='my_bool_of_string'%28List.nth'l'7%29;!autofisica'='my_bool_of_string'%28List.nth'l'8%29;!fisica'='my_bool_of_string'%28List.nth'l'9%29;!profissaorisco'='risco_of_string'%28List.nth'l'10%29!$6!in!List.map'senior_of_list'll;;!!!%28*'fun%c3%a7%c3%a3o'que'cria'uma'lista'de'riscos'a'partir'de'uma'lista'de'seniores'*%29!%28*'a'lista'de'riscos'tem'exatamente'a'mesma'dimens%c3%a3o'e'ordem'da'lista'de'seniores'*%29!let'create_risco_list'sl'=!%28*'A'fun%c3%a7%c3%a3o'decide_risco'decide'qual'o'grau'de'risco'correspondente'a'cada'senior'*%29!let'decide_risco's'='match's'with!$5'$4!ndoencas;!nmedicamentos;!doenca'='true;!autonomia'='false;!autofisica'='false;!profissaorisco!$6'when'ndoencas'$.'2'&&'nmedicamentos'$.'3'&&'%28profissaorisco'='Alto'$5$5'profissaorisco'='Medio%29'-$.'Alto!$5'$4!ndoencas;!nmedicamentos;!desportoj'='false;!fisica'='false;!profissaorisco!$6'when'ndoencas'$-='2'&&'nmedicamentos'$-='3'&&'%28profissaorisco'='Medio'$5$5'profissaorisco'='Baixo%29'-$.'Medio!$5'$4!nmedicamentos;!acidente'='false;!doenca'='false;!sozinho'='false;!profissaorisco'='Baixo!$6'when'nmedicamentos'$-='2'-$.'Baixo!$5'_'-$.'Inconclusivo!in!List.map'decide_risco'sl;;!!!%28*'fun%c3%a7%c3%b5es'para'impress%c3%a3o'de'uma'tabela'na'consola'*%29!let'print_aster'%28%29'='printf'$%28**********************************$0n$%28;;!let'print_header'%28%29'='printf'$%28*''''Utente'''''*''''''Risco'''''*$0n$%28;;!!!%28*'fun%c3%a7%c3%a3o'que'toma'como'argumentos'um'senior'e'um'risco'a'ele'associado'e'imprime'na'consola'o'n%c3%bamero'de'utente'do'senior'e'qual'o'respetivo'grau'de'risco'*%29!let'print_risco's'r'='printf'$%28*''$+10d'''*''$+12s''*$0n$%28's.nutente'%28string_of_risco'r%29;;!!!%28*'fun%c3%a7%c3%a3o'que'itera'conjuntamente'a'lista'de'seniores'e'a'lista'de'riscos'associada'e'chama'a'fun%c3%a7%c3%a3o'print_risco'a'cada'itera%c3%a7%c3%a3o'*%29!let'print_all'rl'sl'=!let'f's'r'='print_risco'r's'in!List.iter2'f'rl'sl;;!!!!%28*'fun%c3%a7%c3%a3o'principal'que'executa'de'facto'o'programa'*%29!let'main'=!%28*'let'm_string_list'='read_lines'file'in'*%29!let'm_string_list'='input'in!let'm_list_list'='create_list_list'm_string_list'in!let'm_filtered_list'='filter_list_by_dim'm_list_list'in!let'm_senior_list'='create_senior_list'm_filtered_list'in!let'm_risco_list'='create_risco_list'm_senior_list'in!begin!print_aster'%28%29;!print_header'%28%29;!print_aster'%28%29;!print_all'm_risco_list'm_senior_list;!print_aster'%28%29!end;;).