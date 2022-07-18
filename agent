:- dynamic ([breeze/1,
             stench/1,
             gold/1,
             wumpus/1,
             safe/1,
             pit/1,
             isWumpus/1,
             isPit/1,
             isGold/1,
             agentSite/1]).

adjacentTo([X,Y],Site) :- (X<4)->  Xright is X+1, Site=[Xright,Y].
adjacentTo([X,Y],Site) :- (X>1)->  Xleft is X-1, Site=[Xleft,Y].
adjacentTo([X,Y],Site) :- (Y<4)->  Yup is Y+1, Site=[X,Yup].
adjacentTo([X,Y],Site) :- (Y>1)->  Ydown is Y-1, Site=[X,Ydown].


breeze([X,Y]) :- (isPit(PitSite),adjacentTo([X,Y],PitSite))->  
    format('There is a Breeze in room ~p!~n',[[X,Y]]); 
    format('There is NO Breeze in room ~p!~n',[[X,Y]]).

stench([X,Y]) :- (isWumpus(Loc),adjacentTo([X,Y],Loc))->  
    format('There is a Stench in room ~p!~n',[[X,Y]]); 
    format('There is NO Stench in room ~p!~n',[[X,Y]]).

pit([X,Y]) :- forall(adjacentTo([X,Y],Site), (breeze(Site))), (isPit([X,Y]))-> 
    		format('There is a Pit in room ~p!~n',[[X,Y]]); 
    		format('There is NO Pit in room ~p!~n',[[X,Y]]).

wumpus([X,Y]) :- forall(adjacentTo([X,Y],Site), stench(Site)),isWumpus([X,Y]) ->
    		format('Wumpus IS in room ~p!!~n',[[X,Y]]); 
    		format('Wumpus IS NOT in room ~p.~n',[[X,Y]]).

safe([X,Y]):- \+ isPit([X,Y]), \+ isWumpus([X,Y]) ->  
    		format('~p is safe!!~n',[[X,Y]]); 
    		format('~p is not safe!!~n',[[X,Y]]). 

grabGold():- write('Gold is yours!').


gold([X,Y]):- (isGold([X,Y]))->  
    grabGold(); 
    format('No Gold found here!').


shootWumpus([X,Y]):- (isPit([X,Y]))->
    format('Agent fell in the pit');
 
    (isWumpus(Site), adjacentTo([X,Y],Site))
    -> 	format('Wumpus killed in ~p!!~n',[Site]); 
    (isWumpus([X,Y]))
    ->  format('Wumpus is here, hard luck!');
    	format('No Wumpus found in adjacent rooms.').


start:-
    init,
    assert(agentLocation([1,1])).

init:-    % uncomment one of the following scenarios before testing the code:
      
	% Scenario 1
    %retractall(isGold(_)),
    %assert(isGold([3,1])),
    %retractall(isWumpus(_)),
    %assert(isWumpus([2,1])),
    %retractall(isPit(_)),
    %assert(isPit([1,4])),
    %assert(isPit([4,3])),
    %retractall(agentSite(_)).

    
    % Scenario 2
   	%retractall(isGold(_)),
    %assert(isGold([2,3])),
    %retractall(isWumpus(_)),
    %assert(isWumpus([1,3])),
    %retractall(isPit(_)),
    %assert(isPit([3,3])),
    %assert(isPit([3,1])),
    %retractall(agentSite(_)).

    
    % Scenario 2
    %retractall(isGold(_)),
    %assert(isGold([4,1])),
    %retractall(isWumpus(_)),
    %assert(isWumpus([3,1])),
    %retractall(isPit(_)),
    %assert(isPit([4,2])),
    %assert(isPit([4,3])),
    %assert(isPit([3,4])),
    %assert(isPit([1,3])),
    %retractall(agentSite(_)).

