
class flervalgsporsmol:
    def __init__(self, prompt, svar):
        self.prompt = prompt
        self.svar = svar
         
    def __str__(self):
        return self.prompt
    
    def sjekk_svar(self, alt):
        return alt == self.svar
    
sporsmaalliste = []
with open("sporsmaalsfil.txt","r",encoding = "UTF-8") as fila:
        for linje in fila:
            split = linje.split(":")
            sporsmaal = split[0]
            alt = split[2].strip("[]\n ").split(",")
            svar = split[1].strip(' ')
            prompt = f"{sporsmaal}\n"
            for i, a in enumerate(alt):
                prompt += f"{i}: {a}\n"
            sporsmaalliste.append(flervalgsporsmol(prompt, svar))
            
def kjør_quiz():
    for sporsmol in sporsmaalliste:       
        if sporsmol.sjekk_svar(input(sporsmol)):
            print("Riktig!")
        else:
            print("Feil!")
kjør_quiz()
