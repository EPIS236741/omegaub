#ifndef TIME5_H
#define TIME5_H

class Time {
public:
    Time( int = 0, int = 0, int = 0 );
    void setTime( int, int, int );
    void setHour( int );
    void setMinute( int );
    void setSecond( int );
    int getHour() const;
    int getMinute() const;
    int getSecond() const;
    void printMilitary() const;
    void printStandard() const;
    
private:
    int hour;
    int minute;
    int second;
};

#endif

#include <iostream>
using std::cout;
//#include "time5.h"

Time::Time( int hr, int min, int sec )
    { setTime( hr, min, sec ); }

void Time::setTime( int h, int m, int s )
{
    setHour( h );
    setMinute( m );
    setSecond( s );
}

void Time::setHour( int h )
    { hour = ( h >= 0 && h < 24 ) ? h : 0; }

void Time::setMinute( int m )
    { minute = ( m >= 0 && m < 60 ) ? m : 0; }

void Time::setSecond( int s )
    { second = ( s >= 0 && s < 60 ) ? s : 0; }

int Time::getHour() const { return hour; }

int Time::getMinute() const { return minute; }

int Time::getSecond() const { return second; }

void Time::printMilitary() const
{
    cout << ( hour < 10 ? "0" : "" ) << hour << ":"
         << ( minute < 10 ? "0" : "" ) << minute << " ";
}

void Time::printStandard() const
{
    cout << ( ( hour == 12 ) ? 12 : hour % 12 ) << ":"
         << ( minute < 10 ? "0" : "" ) << minute << ":"
         << ( second < 10 ? "0" : "" ) << second
         << ( hour < 12 ? " AM" : " PM" );
}

//#include "time5.h"

int main()
{
    Time wakeUp( 6, 45, 0 );
    const Time noon( 12, 0, 0 );
    
    wakeUp.setHour( 18 );
    //noon.setHour( 12 );
    wakeUp.getHour();
    noon.getMinute();
    noon.printMilitary();
    noon.printStandard();
    
    return 0;
}
