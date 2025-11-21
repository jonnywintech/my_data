module.exports.add = add ;
exports = { add, PI, substract };

// adding directory to exports

ako se importuje direktorijum onda mora imate index.js fajl u tom direktorijumu
u index.js fajlu morate da exportujete sve sto zelite da exportujete. Tacnije importuju se svi fajlovi( math.js > PI , add(var), substract) i onda ih exportujemo u indexu ako zelimo i to u array koji [{PI}] sarzi objekte iz fajlova.