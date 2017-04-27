# Algoritm-ID3
Library for ID3 algorithm


# Using the library
1. Create object Data<br>
  Data x = new Data();
2. Add the list of attributes as List<string><br>
  x.Attr = your List of attributes
3. Add the list of rows as List<Dictionary<string, string>><br>
  Dictionary<key, value> - key:attribute; value:value of the attribute in this row<br>
  And so you add to Dictionary the whole row<br><br>
  x.Rows = your List of rows <br>
    or<br>
  x.Rows.Add(Dictionary<string, string>);
4. Сall the function StartAlgorythm()<br>
  x.StartAlgorythm();
5. Take the result string<br>
  string result = x.Result;
  
# Example:
    Data x = new Data();
    List<string> attr = x.Attr = new List<string> { "Wiek", "Wada_wzroku", "Astygmatyzm", "Lzawienie", "SOCZEWKI" };
    
    Dictionary<string, string> row1 = new Dictionary<string, string>();
    row1.Add("Wiek", "mlody");
    row1.Add("Wada_wzroku", "krotkowidz");
    row1.Add("Astygmatyzm", "nie");
    row1.Add("Lzawienie", "normalne");
    row1.Add("SOCZEWKI", "miekkie");
    
    ...
    
    x.Rows.Add(row1);
    x.Rows.Add(row2);
    ...
    
    x.StartAlgorythm();
    string result = x.Result;
    
# Data to test
    [ Wiek
    Wada_wzroku
    Astygmatyzm
    Lzawienie
    SOCZEWKI ]

  mlody       krotkowidz  nie         normalne    miekkie     
  mlody       dalekowidz  tak         normalne    twarde      
  mlody       dalekowidz  nie         zmniejszone brak        
  mlody       krotkowidz  tak         zmniejszone brak        
  prestarczy  krotkowidz  tak         zmniejszone brak        
  prestarczy  krotkowidz  nie         normalne    miekkie     
  mlody       krotkowidz  tak         normalne    twarde      
  starczy     dalekowidz  tak         zmniejszone brak        
  prestarczy  dalekowidz  nie         zmniejszone brak        
  prestarczy  dalekowidz  tak         zmniejszone brak        
  starczy     krotkowidz  tak         normalne    twarde      
  prestarczy  dalekowidz  nie         normalne    miekkie     
  starczy     dalekowidz  tak         normalne    brak        
  starczy     krotkowidz  tak         zmniejszone brak        
  starczy     krotkowidz  nie         normalne    brak        
  prestarczy  krotkowidz  tak         normalne    twarde      
  mlody       krotkowidz  nie         zmniejszone brak        
  starczy     krotkowidz  nie         zmniejszone brak        
  starczy     dalekowidz  nie         zmniejszone brak        
  mlody       dalekowidz  nie         normalne    miekkie     
  starczy     dalekowidz  nie         normalne    miekkie     
  prestarczy  dalekowidz  tak         normalne    brak    
  
 # Example of result: 
    1.Lzawienie:normalne-->2.Astygmatyzm:nie-->3.Wiek:mlody is miekkie-count:2
    1.Lzawienie:normalne-->2.Astygmatyzm:nie-->3.Wiek:prestarczy is miekkie-count:2
    1.Lzawienie:normalne-->2.Astygmatyzm:nie-->3.Wiek:starczy-->4.Wada_wzroku:krotkowidz is brak-count:1
    1.Lzawienie:normalne-->2.Astygmatyzm:nie-->3.Wiek:starczy-->4.Wada_wzroku:dalekowidz is miekkie-count:1
    1.Lzawienie:normalne-->2.Astygmatyzm:tak-->3.Wada_wzroku:dalekowidz-->4.Wiek:mlody is twarde-count:1
    1.Lzawienie:normalne-->2.Astygmatyzm:tak-->3.Wada_wzroku:dalekowidz-->4.Wiek:starczy is brak-count:1
    1.Lzawienie:normalne-->2.Astygmatyzm:tak-->3.Wada_wzroku:dalekowidz-->4.Wiek:prestarczy is brak-count:1
    1.Lzawienie:normalne-->2.Astygmatyzm:tak-->3.Wada_wzroku:krotkowidz is twarde-count:3
    1.Lzawienie:zmniejszone is brak-count:10
