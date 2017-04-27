# Algoritm-ID3
Library for ID3 algorithm


# Using the library
1. Create onject Data
  Data x = new Data();
2. Add the list of attributes as List<string>
  x.Attr = your List of attributes
3. Add the list of rows as List<Dictionary<string, string>>
  x.Rows = your List of rows
4. Сall the function StartAlgorythm()
  x.StartAlgorythm();
5. Take the result
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
