# Ciclo for decreciente

	ORG $0000
	LDAA #$03
	LDX #$FB00

LOOP ADDA #$30
	STAA 0,X
	SUBA #$30
	INX
	DECA
	BNE LOOP